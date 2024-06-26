# Super Mario Exercise
## Author: Carlo Tacchella

## Request
This exercise is based on the famous Super Mario game.
Brief Game Rules
1. R1 Super Mario, is our hero, he springs around the world, takes all the Coins he meets.
2. R2 Super Mario has enemies. If an enemy kills Super Mario, a life is lost. When all lives have been lost, the game ends.
3. R3 Super Mario can get extra lives by jumping each enemy consecutively without touching the ground.
4. R4 Super Mario can earn 50 coins by defeating enemies with fireballs.
5. R5 When Mario reaches 1000 points, he gets an additional life.

## Example "A"
If you have: "ConsecutivelyJumpOnBanzai_Bill,FireballOnBanzaiBill, Coin,Coin,Coin,ConsecutivelyJumpOnBlargg,InvincibleBig_Boo"
you earn 200+50+10+10+10+1600 points, but you lose a life but... 1600 = 600 points+1 life so you earn 600+280 points without loosing a life.

## Scoring System

### Get a single Coin
10 Points

### Consecutively jump on enemies
- Banzai_Bill: 200 points
- Beach_Koopa: 400 points
- Big_Boo: 800 points
- Blargg: 1600 points

### Fireball
50 Points based on "Example A"

## About this Project
I choose to develop the project in Java 22.

## Assumptions
- I will remove points to get a life every time points gained are over 1000.
- I will ALWAYS assume that default points value is 2000 and life default value is 3
- I will assume that fireball earning coins are 50 basing on example A and not 5 as written in R4 on given text.

## Pattern design used
- Creational Pattern Design "Build" in ConsecutivelyJump.java

## About the testing
I used JUnit5.8.1 and I placed the tests in the package test.

## Example of input
In file "SuperMario-seq.txt"
"ConsecutivelyJumpOnBanzai_Bill,FireballOnBanzai_Bill,Coin,Coin,Coin,Coin,Coin,InvincibleBig_Boo,FireballOnBanzai_Bill,InvincibleBlargg,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,FireballOnBanzai_Bill,ConsecutivelyJumpOnBeach_Koopa,ConsecutivelyJumpOnBig_Boo,InvincibleBeach_Koopa,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin,Coin"

## Type of inputs:

### ConsecutivelyJumpOn<Monster type>
Effects: 
Point increment based on "Scoring system", based on the monster type.
If points > 1000 Life count +1 and points-=1000 (as shown in "Example A").
This behavior ensures that the score is never higher than the initial value + 999.
Basing on R3 if we have previous action "ConsecutivelyJumpOn" 
we increment the life count by one,
assuming other actions involve Mario touching the ground.

### Invincible<Monster type>
Life count: -1
If Life count reaches 0 the game is marked as "Fail"

### FireballOn<Monster type>
Effects: 5 points
If points > 1000 Life count +1 and points -=1000

### Coin
Effects: 10 points
If points > 1000 Life count +1 and points -=1000
