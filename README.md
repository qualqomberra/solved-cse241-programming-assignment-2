Download Link: https://assignmentchef.com/product/solved-cse241-programming-assignment-2
<br>
<h1>Description</h1>

<ul>

 <li>This is an individual assignment. Please do not collaborate</li>

 <li>If you think that this document does not clearly describes the assignment, ask questions before its too late.</li>

</ul>

This assignment is about designing, implementing and testing classes for the following setup:

<ul>

 <li>A small version of the game called Tsuro will adapted for the command line interface.</li>

</ul>

<strong>Tsuro</strong>

<ul>

 <li>Read the explanations about the original game (https://en.wikipedia.org/wiki/Tsuro)</li>

</ul>

<strong>Basic Elements of the Game</strong>

<h2>Tokens</h2>

<ul>

 <li>Tokens represent players.</li>

 <li>For the version you are going to implement, tokens will be displayed as single characters.</li>

</ul>

<h2>Path Cards</h2>

<ul>

 <li>Square cards which have 2 ports on each of their sides and various routing information.</li>

 <li>You can display a Path card as follows:</li>

</ul>

….1..2….

:      8 6          : 8           1 5    3 7          4 7          4

:         2 3          :

….6..5….

<ul>

 <li>Here, ports are numbered (1,2,3,4,5,6,7,8).</li>

 <li>Inside, the routing information is presented. For the particular card above:

  <ul>

   <li>port 8 is connected to port 1</li>

   <li>port 7 is connected to port 4</li>

   <li>port 6 is connected to port 2</li>

   <li>port 5 is connected to port 3</li>

  </ul></li>

 <li>Connections are not directed.</li>

 <li>A path card can be rotated clockwise or counter-clockwise(repeatedly)</li>

</ul>

<h2>2D grid</h2>

<ul>

 <li>This game will be played on a 2D grid.</li>

 <li>Each cell on this grid will either be occupied by a path card or it will be empty.</li>

 <li>Cards can only be placed in empty cells</li>

 <li>Below is an example of a partially filled 3×3 grid</li>

</ul>

——o–o——–o–o——–o–o——

| ….1..2……..7..8….                                           |

| :   8 6          ::             1 6          :               | o 8       1 5          36       8 7          1              o o 7       4 7          45           3 4          2       o | :        2 3          ::             2 5          :               | | ….6..5……..4..3….         |

| ….3..4….                                                                 |

| :   4 3          :               | o 2       1 6          5              o o 1       2 5       6              o | :        7 8          :               | | ….8..7….           | | ….1..2……..1..2……..1..2…. |

| : 5 6 :: 6 5 :: 8 6 : | o 8 4 7 38 3 8 38 1 5 3 o o 7 3 8 47 4 7 47 4 7 4 o | : 2 1 :: 1 2 :: 2 3 : | | ….6..5……..6..5……..6..5…. |

——o–o——–o–o——–o–o——

<ul>

 <li>On the sides of the grid ‘o’s represent exit/entry ports of the game.</li>

 <li>A User token may start at any of the exit/entry ports and exit from any of the ports.</li>

 <li>If the ports of path cards(tiles) collide, they are assumed to be connected. For example, port 3 of the tile 1 (first row, first column) is connected to port 6 of the tile on the right.</li>

</ul>

<h2>Rules of The Game</h2>

<ul>

 <li>For a general understanding of the game please read the necessary wikipedia articles. You can find more information on other webpages.</li>

 <li>Basically:

  <ul>

   <li>It is a turn-based game.</li>

   <li>There are at least 2 players, each one has a token.</li>

   <li>Game starts randomly. (random entry ports are chosen for each player) <strong>– </strong>Initially, the 2D grid is empty.</li>

   <li>Each player is given a set of cards(Generally 3 cards.)</li>

   <li>A turn starts with the player deciding on a card(selecting a card from the set given). If the set of cards is empty, a new set is requested (how you generate a set is up to you. It has to be flexible for further modifications. So hide unnecessary details.)</li>

   <li>Once a card is selected, it is placed in an empty cell on the 2D grid.</li>

   <li>The token follows the route on the card placed.</li>

   <li>The objective is to remain on the game.</li>

  </ul></li>

</ul>

<strong>Example:</strong>

<ul>

 <li>Player1(token X) places a path card:</li>

</ul>

——X–o——–o–o——–o–o——

| ….1..2….                                                                 |

| :   8 6          :               | o 8       1 5          3              o Y 7       4 7       4              o | :        2 3          :               | | ….6..5…            |

|     | |           | o           o o          o |           | |           | |           | |       | o           o o          o |           | |           |

——o–o——–o–o——–o–o——

<ul>

 <li>With the tile which is recently placed, the game advances. X follows the path and exist the game(loses). Y follows its path and waits for the next event.</li>

 <li>It’s Player2(token Y)’s turn:</li>

</ul>

——o–o——–o–o——–o–o——

| ….1..2….                                                                 |

| :   8 6          :               | X 8       1 5          3              o o 7       4 7       Y              o | :        2 3          :               | | ….6..5…            | | ….3..4….        |

| :   4 3          :               | o 2       1 6          5              o o 1       2 5       6              o | :        7 8          :               | | ….8..7….           |

|     | |           | o           o o          o |           | |           |

——o–o——–o–o——–o–o——

<ul>

 <li>At this stage there isn’t any other player, so Y wins.</li>

</ul>

<h1>Implementation</h1>

<ul>

 <li>You have to use OOP principles.</li>

 <li>You cannot use the topics we haven’t covered in class. (you can utilize the tools you know from C programming course)</li>

 <li>For the solution, you may need to create several classes.</li>

 <li>Try to use the concepts such as encapsulation, protecting variables with const keyword, overloading functions/operators,</li>

 <li>Implement the whole game as a class and write necessary constructors for the cases such as player vs player, 3 players against each other etc…(for this you may need to have a player class as well.)</li>

 <li>This document does not fully describes the visualization of the game flow. Create necessary dialogs such as displaying set of cards to the user, asking user choice, presenting the state of the game, etc… It is your responsibility to create an appropriate flow so that the game can be played.</li>

</ul>