Download Link: https://assignmentchef.com/product/solved-cs3610-project-5
<br>
<h2>Shortest-path algorithm and implementations</h2>

In order to find a single source shortest path, you are asked to implement Dijkstra’s algorithm described in lecture (the powerpoint Ch12 part2.pptx is attached in this assignment). If you recall, <strong>the array version </strong>of Dijkstra’s algorithm runs in <em>O</em>(<em>V </em><sup>2</sup>+<em>E</em>) time, where <em>V </em>is the number of vertices in the graph and <em>E </em>is the number of edges. The <em>O</em>(<em>V </em><sup>2</sup>) component refers to the number of operations carried out to find every minimum distance vertex extracted from the set of unvisited vertices at the beginning of each iteration of the while loop. The <em>O</em>(<em>E</em>) component results from comparing and possibly updating the distances of all vertices adjacent to the minimum distance vertices. In other words, the for loop within the while loop runs <em>O</em>(<em>E</em>) operations in total.

<strong>Heap version </strong>If your graph is not too dense (meaning the graph does not contain an overwhelming number of edges), you may want to consider storing the set of unvisited vertices in a min heap using distance to the source vertex as a key. This will help you find all the minimum distance vertices extracted at the beginning of each iteration of the while loop in <em>O</em>(<em>V </em>log(<em>V </em>)) time as opposed to <em>O</em>(<em>V </em><sup>2</sup>) time. Of course, when you now update the distance of a neighboring vertex in the for loop below, you must also update that vertex’s position in the min heap. As you already know, bubbling up an element in a min heap of <em>n </em>elements takes just <em>O</em>(log(<em>n</em>)) time, but the initial searching for the element takes <em>O</em>(<em>n</em>) time. In order to avoid the <em>O</em>(<em>n</em>) search, you must implement a lookup table that returns a vertex’s index in the min heap in <em>O</em>(1) time. If implemented correctly, the cumulative time complexity of updating the distance values of vertices in the min heap version of Dijkstra’s would be <em>O</em>(<em>E </em>log(<em>V </em>)). In other words, using a lookup table and a min heap, the for loop within the while loop runs in <em>O</em>(<em>E </em>log(<em>V </em>)) time as opposed to the <em>O</em>(<em>E</em>) time seen in the version of Dijkstra’s algorithm described in the previous paragraph. Thus, the total time complexity of this modified Dijkstra’s algorithm is <em>O</em>(<em>V </em>log(<em>V </em>) + <em>E </em>log(<em>V </em>)). As said early, it is more advantageous to use the min heap version if your graph is sparse.

<strong>Lookup table and min-heap: </strong>There could be different ways to implement this lookup table. One setup could be an array of pointers, where each element stores the address of the corresponding vertex in the min-heap. In order to communicate back to the lookup table, the elements in the min-heap should be designed as the combinations of (distance, vertex-index) or (distance, vertex-index, predecessor), which is similar to the ($179B, Washington) setup in Project 4. In project 4, I suggested you use STL’s <em>priority queue </em>to implement your max-heap. In this project, however, you may have to implement a heap class by yourself, as the needed operations are not available in STL <em>priority queue </em>or <em>heap</em>.

<h2>Assignment and Bonus</h2>

In this project, the 6 final grade points will be awarded if you successfully implement the array version of Dijkstra’s algorithm, as described in lecture. If you successfully implement the min heap version, you will be awarded the 6 final grade points plus 3 bonus points. For the students who decide to implement the heap version, I would suggest you start with the array version for a correct baseline. Also, please include a note in your submission to inform the TA that your implementation is the heap version.

<h1>Input</h1>

Input is read from the keyboard. <strong>The first line of input is the number of test cases </strong><em>K</em>. Each of the <em>K </em>test cases is written in the following format:

<h3>Individual Test Case Format</h3>

<table width="586">

 <tbody>

  <tr>

   <td width="586">n city1 city2 .. .city nd 11 d 12 … d1n d 21 d 22 … d2n...d n1 d n2 … d nn</td>

  </tr>

 </tbody>

</table>

The first line of each test case is the number of cities <em>n </em>in the graph. The next <em>n </em>lines are the names of each city. City names consist only of alphabetic characters. Following the list of <em>n </em>city names is an <em>n</em>x<em>n </em>distance matrix where each distance d ij is an integer value in the range [0<em>,</em>10000] representing the distance of the road connecting city <em>i </em>to city <em>j</em>. A distance d ij = 0 indicates that there does not exist any road connecting city <em>i </em>to city <em>j</em>. For this project, all roads will be undirected, which means d ij = d ji for all cities <em>i </em>and <em>j</em>. As a result, every input distance matrix will be symmetric.

<h1>Output</h1>

For each test case, output a space delimited list of all the city names in the shortest path connecting city 1 and city n followed by the integer distance of the path. City names should be listed in order of when they are to be visited starting from city 1 and ending with city n. If city 1 has multiple shortest paths to city n, just output one of them. Also note that in every test case, there will always be a path connecting city 1 to city n.

<h2>Sample Test Cases</h2>

Use input redirection to redirect commands written in a file to the standard input, e.g.

$ ./a.out &lt; input1.dat.

<h3>Input 1</h3>

1

4

Akron

Athens

Columbus

Cleveland

<ul>

 <li>1 2 0</li>

 <li>0 5 6</li>

 <li>5 0 7</li>

</ul>

0 6 7 0

<strong>Output 1</strong>

Akron Athens Cleveland 7

<ul>

 <li></li>

</ul>