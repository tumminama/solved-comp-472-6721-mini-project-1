Download Link: https://assignmentchef.com/product/solved-comp-472-6721-mini-project-1
<br>
<strong>Purpose</strong>:           The purpose of this project is to make you practice and experiment with heuristic search.




<strong>Heuristic Search </strong>

<strong> </strong>

Assume a variation of the 8-puzzle called 11d-puzzle.  The 11d-puzzle is identical to the 8-puzzle, except for 2 differences:

<ol>

 <li>the board is a 3×4</li>

 <li>diagonal moves into the empty tile are legal (assume it can be done on a physical board). So we have</li>

</ol>

at most 8 possible moves: UP, UP –RIGHT, RIGHT, DOWN–RIGHT, DOWN, DOWN–LEFT, LEFT, UP–LEFT.




The goal configuration of the 11d-puzzle is:




<table width="142">

 <tbody>

  <tr>

   <td width="35">1</td>

   <td width="36">2</td>

   <td width="35">3</td>

   <td width="36">4</td>

  </tr>

  <tr>

   <td width="35">5</td>

   <td width="36">6</td>

   <td width="35">7</td>

   <td width="36">8</td>

  </tr>

  <tr>

   <td width="35">9</td>

   <td width="36">10</td>

   <td width="35">11</td>

   <td width="36">0</td>

  </tr>

 </tbody>

</table>




To represent the positions on the board, let us use the letters <strong>a</strong> to <strong>l</strong> as indicated by the superscripts below:




<table width="142">

 <tbody>

  <tr>

   <td width="36">1<strong>a</strong></td>

   <td width="35">2<strong>b</strong></td>

   <td width="35">6<strong>c</strong></td>

   <td width="35">4<strong>d</strong></td>

  </tr>

  <tr>

   <td width="36">5<strong>e</strong></td>

   <td width="35">9<strong>f</strong></td>

   <td width="35">7<strong>g</strong></td>

   <td width="35">3<strong>h</strong></td>

  </tr>

  <tr>

   <td width="36">0<strong><sup>i</sup></strong></td>

   <td width="35">10<strong>j</strong></td>

   <td width="35">11<strong>k</strong></td>

   <td width="35">8<strong>l</strong></td>

  </tr>

 </tbody>

</table>

For example, in the figure on the left:

tile #1 is at position <strong>a</strong>, …

tile #6 is at position <strong>c</strong>, …

<sub>                                                                               </sub>the empty tile (denoted by the 0) is at position <strong>i</strong>…




Since a tile can only move into the empty position, all that is required to represent a move is to record the tile that moved.  For example, given the configuration above, the sequence of moves: <strong>[f g k]</strong> should be interpreted as:

<ol>

 <li>move tile <strong>f</strong> DOWN–LEFT to position <strong>i</strong> (where the empty tile is)</li>

 <li>(now the empty tile is at position <strong>f</strong>) move tile <strong>g</strong> LEFT to position <strong>f</strong></li>

 <li>(now the empty tile is at position <strong>g</strong>) move tile <strong>k</strong> UP to position <strong>g</strong></li>

</ol>




<strong>Your task: </strong>

Implement a solution for the 11d-puzzle using the following 3 search algorithms:

<ol>

 <li>Depth-first search (DFS)</li>

 <li>Best-first search (BFS)</li>

 <li>Algorithm A* (A*)</li>

</ol>




Ties between equivalent nodes should be broken in a clockwise direction starting with UP.  This means that equivalent moves are ordered this way:

<h1>UP &gt;  UP –RIGHT  &gt;  RIGHT  &gt;  DOWN- RIGHT  &gt;  DOWN  &gt;  DOWN –LEFT  &gt;  LEFT &gt; UP–LEFT</h1>

<em>(most preferred moves)</em>                                                                        <em>(least preferred moves)</em>




For BFS and A*, you must experiment with 2 different heuristics <em>h1</em> and <em>h2 </em>of your choice.  <em>h1</em> and <em>h2</em> should both be used with BFS and with A*.

<strong>Input: </strong>

Your program will read from the console an initial puzzle, where each tile will be represented by a unique integer (0 to 11), where the zero will denote the empty tile. The order of the tiles will follow the alphabetic order of the tile names (<strong>a b c d e f g h i j k l</strong>). For example, the puzzle:




<table width="114">

 <tbody>

  <tr>

   <td width="28">1</td>

   <td width="29">0</td>

   <td width="29">3</td>

   <td width="28">7</td>

  </tr>

  <tr>

   <td width="28">5</td>

   <td width="29">2</td>

   <td width="29">6</td>

   <td width="28">4</td>

  </tr>

  <tr>

   <td width="28">9</td>

   <td width="29">10</td>

   <td width="29">11</td>

   <td width="28">8</td>

  </tr>

 </tbody>

</table>




will be represented as:  <strong>1 0 3 7 5 2 6 4 9 10 11 8 </strong>

<strong> </strong>

<strong>Output: </strong>

Given an initial puzzle (from the console), your program must output its results in the 5 text files below:




<ol>

 <li><strong>txt</strong>:</li>

</ol>

A trace of the puzzle configuration after each move on the final solution found by depth-first search.   First, you display the initial configuration preceded by a 0 (zero), then for each move in the solution path, you should display the move followed by the new configuration in list format, one puzzle per line.  For example, if your final solution path is:

<strong>[c d h l k g c d b f k l]  </strong>

Then <strong>puzzleDFS.txt</strong> should contain:




<strong>0 [1, 0, 3, 7, 5, 2, 6, 4, 9, 10, 11, 8] </strong><em>// 0 then the initial configuration </em><strong>c [1, 3, 0, 7, 5, 2, 6, 4, 9, 10, 11, 8] </strong><em>// move c, then configuration after move c </em><strong>d [1, 3, 7, 0, 5, 2, 6, 4, 9, 10, 11, 8] </strong><em>// move d, then configuration after move d </em><strong>h [1, 3, 7, 4, 5, 2, 6, 0, 9, 10, 11, 8] </strong><em>// … </em><strong>l [1, 3, 7, 4, 5, 2, 6, 8, 9, 10, 11, 0] k [1, 3, 7, 4, 5, 2, 6, 8, 9, 10, 0, 11] g [1, 3, 7, 4, 5, 2, 0, 8, 9, 10, 6, 11] c [1, 3, 0, 4, 5, 2, 7, 8, 9, 10, 6, 11] d [1, 3, 4, 0, 5, 2, 7, 8, 9, 10, 6, 11] b [1, 0, 3, 4, 5, 2, 7, 8, 9, 10, 6, 11] f [1, 2, 3, 4, 5, 0, 7, 8, 9, 10, 6, 11] k [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 0, 11] l [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 0]  </strong>




Please follow the format indicated above.




<ol start="2">

 <li><strong>puzzleBFS-h1.txt</strong>: same as above but for BFS with heuristic<em> h1</em>.</li>

 <li><strong>puzzleBFS-h2.txt</strong>: same as above but for BFS with heuristic <em>h2</em>.</li>

 <li><strong>puzzleAs-h1.txt</strong>: same as above but for A* with heuristic<em> h1</em>. <strong>puzzleAs-h2.txt</strong>: same as above but for A* with heuristic <em>h2</em>.</li>

</ol>

<strong> </strong>

<strong>Programming Environment: </strong>

You can use Java, C, C++, Python or Prolog.  If you wish to use another language, please check with me first.

<strong> </strong>

<strong>Experimentations: </strong>

Note that this is a mini-project, not an assignment.  The difference is that it is open-ended and in addition to the required work stated above, you are expected to be creative, perform additional experimentations and analyse the results of your experimentations.  Examples of experimentations include trying different heuristics, modifying the size or rules of the puzzle,…




<strong>The Code: </strong>

Submit all files necessary to run your code in addition to a <strong>README.txt </strong>which will contain specific and complete instructions how to run your program on the desktops in the computer labs.  If the instructions in your readme file do not work or are incomplete, you will not be given the benefit of the doubt.

<strong> </strong>

<strong> </strong>











