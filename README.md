# Rock Paper Scissor Game with Python & Turtle

This project is part of the course "Online Diploma in Python Programming" of IBAT College Dublin and is the first assignment of the course.

The proposal is to make a quick program using Turtle to show our abilities and the knowledge of all content present during the first classes.

In my project I choose to create a "Rock, Paper and Scissors Game". For that I will use my knowledge in function, for and while loops, inputs, variables and, as the most important here, turtles.

I divided the project in 3 parts:

- Create the Turtle
- Create the logical part of the game.
- Put everything together!

And after that I put everything together.

I hope you enjoy!

Let's play?

Good luck!!!

```python
# Importing the libraries that we will use for the game.
import random
import turtle
import time
```

```python
#Setting the background
screen = turtle.Screen()
screen.bgcolor("white")
screen.title("Rock, Paper and Scissors Game")
screen.setup(width=500, height=500)
```

## Making the things interesting!
To make the things interesting and practice the For and While Loops, I chose to draw on the screen the "weapon" that the player and opponent chose. For that I created these three functions below.

```python
def rock():
    rock = turtle.Turtle()
    rock.hideturtle()
    rock.pensize(3)
    rock.speed(20)

    fwr = 25
    turn = 90

    count = 0
    while (count < 1125):     
        count = count + 25
        rock.forward(fwr)
        rock.left(turn)
        rock.right(turn)

        if count == 50:
            rock.lt(turn)
        elif count == 75:
            rock.lt(turn)
        elif count == 150:
            rock.lt(turn)
        elif count == 225:
            rock.lt(turn)
        elif count == 325:
            rock.lt(turn)
        elif count == 500:
            rock.lt(turn)
        elif count == 525:
            rock.lt(turn)
        elif count == 625:
            rock.rt(turn+90)
        elif count == 675:
            rock.lt(turn)
        elif count == 700:
            rock.lt(turn)
        elif count == 750:
            rock.rt(turn+90)
        elif count == 800:
            rock.lt(turn)
        elif count == 825:
            rock.lt(turn)
        elif count == 875:
            rock.rt(turn+90)
        elif count == 975:
            rock.lt(turn)
        elif count == 1000:
            rock.lt(turn)

    time.sleep(5)
    turtle.clearscreen()        
```    

```python
def paper():
    paper = turtle.Turtle()
    paper.hideturtle()
    paper.seth(270)
    paper.pensize(3)
    paper.speed(20)

    fwr = 25
    turn = 90
    
    count = 0
    while (count < 800):     
        count = count + 25
        paper.forward(fwr)

        if count == 50:
            paper.rt(turn)
        elif count == 100:
            paper.rt(turn+40)
        elif count == 175:
            paper.rt(turn-40)
        elif count == 300:
            paper.rt(turn)
        elif count == 500:
            paper.rt(turn)
        elif count == 675:
            paper.rt(turn)

    time.sleep(5)
    turtle.clearscreen() 
```
```python
def scissors():
    scissorsRight = turtle.Turtle()
    scissorsRight.hideturtle()
    scissorsRight.pensize(8)
    scissorsRight.speed(20)
    
    turn = 90

    scissorsLeft = turtle.Turtle()
    scissorsLeft.hideturtle()
    scissorsLeft.pensize(8)
    scissorsLeft.speed(20)

    scissorsRight.circle(-30)
    scissorsRight.goto(-100,140)
    scissorsRight.rt(turn+40)

    scissorsLeft.penup()
    scissorsLeft.goto(-90,0)
    scissorsLeft.pendown()

    scissorsLeft.circle(-30)
    scissorsLeft.goto(-10,140)
    scissorsLeft.rt(turn-40)

    time.sleep(5)
    turtle.clearscreen()
```
## Defining the players
Now we will create the players! 

- The first part is a variable who will receive the player choice with an input text.
- The second "the machine" choice before we use an IF Statement to validated the result

```python
#Creating the variable to receive the player choice
playerChoice = input("Select Rock, Paper or Scissors: ")

'''As python is case sensitive and I don't know how the player will written the game option, 
I chosen convert the input to uppercase before make the IF statement to check the values'''

playerChoice = playerChoice.upper()
```

```python
#Creating the opponent variable that will storage "the machine" choice.
options = ['ROCK','PAPER','SCISSORS']

#The variable "machineChoice" will pick a random item for the options list. I'm using [0] to pick just the value.
machineChoice = random.sample(options, 1)[0] 
```

## Understanding the Logical
"Rock, paper and scissors" is one of the most simple and funny games that ever are created. The basic logic is:
 
- Rock wins to Scissor
- Rock lose for paper
- Paper wins to Rock
- Paper lose for Scissors
- Scissors wins to Paper
- Scissors lose for Rock

So to the logic part of the game I choose to use the library random() to choose the machine part and an IF statement to compare the player option with the machine.

```python
def validationGame(player,machine):
    if player == 'ROCK' and machine == 'SCISSORS' or player == 'PAPER' and machine == 'ROCK' or player == 'SCISSORS' and machine == 'PAPER':
        resultTurtle = turtle.Turtle()
        resultTurtle.hideturtle()
        resultTurtle.color('Green')
        resultTurtle.write('!!!YOU WIN!!!', font=('Helvetica', 50, 'bold'), align='center')
        time.sleep(4)
        turtle.clearscreen()
    elif player == 'ROCK' and machine == 'PAPER' or player == 'PAPER' and machine == 'SCISSORS' or player == 'SCISSORS' and machine == 'ROCK':
        resultTurtle = turtle.Turtle()
        resultTurtle.hideturtle()
        resultTurtle.color('Red')
        resultTurtle.write('...YOU LOSE...', font=('Helvetica', 50, 'bold'), align='center')
        time.sleep(4)
        turtle.clearscreen()
    elif player == 'ROCK' and machine == 'ROCK' or player == 'PAPER' and machine == 'PAPER' or player == 'SCISSORS' and machine == 'SCISSORS':
        resultTurtle = turtle.Turtle()
        resultTurtle.hideturtle()
        resultTurtle.color('Gray')
        resultTurtle.write('The game has finished tied.', font=('Helvetica', 30, 'bold'), align='center')    
        time.sleep(4)
        turtle.clearscreen()
    
    return
```

```python
'''This function will compare the value of the player and machine choice and return the function that 
will draw this choice.''' 

def drawTurtle(item):
    if item == 'ROCK':
        print(rock())
    elif item == 'PAPER':
        print(paper())
    elif item == 'SCISSORS':
        print(scissors())
    return item
```

## Putting all the things together!
This is the last function! The function Gameplay will receive the player and the opponent choice, validate this value and return these choices. Before saying who won the game the values will be drawing on the screen.

```python
def gamePlay(player,machine):
    
    playerTurtle = turtle.Turtle()
    playerTurtle.hideturtle()
    playerTurtle.color('Blue')
    time.sleep(2)
    playerTurtle.write('You had chosen:', font=('Helvetica', 30, 'bold'), align='center')
    time.sleep(4)
    turtle.clearscreen()
    drawTurtle(player)    

    opponentTurtle = turtle.Turtle()
    opponentTurtle.hideturtle()
    opponentTurtle.color('Red')
    time.sleep(2)
    opponentTurtle.write('Your opponent has chosen:', font=('Helvetica', 30, 'bold'), align='center')
    time.sleep(4)
    turtle.clearscreen()
    drawTurtle(machine)
    
    print(validationGame(player,machine))
```

```python
print(gamePlay(playerChoice,machineChoice))
```

## This is the end!
Thanks a lot for playing my version of "Rock, Paper and Scissors Game!", I hope you enjoyed it
