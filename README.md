Decsription of functions and class:

numberOftrees(): In this function we start from the left node and move to the next node and increasing the counter with plus until we get to the left node again 1. Therefore, if T – Number of trees the complexity is O(T). If the heap is nodes with no children then the complexity is O(N).

HeapNode[] create_main_array(int cnt): the function receives an integer cnt. Then, it iterates all over the trees in the heap and gets the node with the buggest rank. Then, it creates an array with the length of max+3 + (int)(Math.log(cnt)/Math.log(2)), when max is the biggest rank. This function is being used only in consolidation and the only parameter that this function uses is T – Number of tree. Therefore the complexity is O(T). If the heap is nodes with no children then the complexity is O(N).

HeapNode link(HeapNode a, HeapNode b): this function updates the pointers of the two nodes, so that in the end the smaller root will be the parent of the bigger root .O(1)

fix_array (HeapNode[] array,HeapNode node): this function receives an array and a node. If the array item in position == node.rank is null, it sets the node as the item. Otherwise, it links the item and the node(new_node) and with recursion it goes to fix_array(array, new_node).O(N)

sort_heap(HeapNode[] array): this function receives an array and iterate every item in the array. If needed that item pointers is changed so that in the end every node next field will be the the following bigger node rank. This function is being used only in consolidation and the array length is not more than O(N). Therefore the complexity is O(N).

private void consolidation(): This function uses numberOftrees(), createarray(), create_main_array() and then it iterates every node in the heap and executes fix_array(). As explained in the class this is O(N). Then, we executes sort_heap(HeapNode[] array). Therefore the complexity is O(N).

deleteMin(): This function delete the parents of all of the children of the minnode. Then, it changes the pointers of the first and last children with minnodeprev and minnodenext. Then it executes consolidation() and findmin. Therefore this O(N).

insertforkMin(int key,HeapNode cnode): This function does the same as insert but it creates an node with value key, in addition to the normal insertion. Therefore it is O(1).
public static int[] kMin(FibonacciHeap H, int k): This function create an array with the length k. then, it creates a new Fibonacci heap (support heap). We iterate k times and in each iteration we find the min from the support heap. Then we insert to the heap the children of the key from the original heap and executes delete min. therefore the complexity is O(k*DEG(k))

isEmpty(): Returns true if and only if the heap is empty, by checking if the minimum Node is null.
O(1)
insert(int key): Creates a node (Heanode) with the given key, and inserts it into the heap.
The new node is added as a subtree root in rank 0 on the left of the heap by changing the pointers of the leftNode and his next node and prev node.
The method returns the new node. O(1).

findMin(): Returns the minimal node (key) of the heap, or null if the heap is empty.
If the method is called from the deleteMin method the method searches for a new minNode by going through all the roots in the heap (the optional minimums) it takes O(n) in worst case and O(log(n)) amortized.
Else, the method retrieves the node from the minNode pointer in O(1) or null if the heap is empty O(1).

Meld(FibonacciHeap heap2): melds heap2 with the current heap. The method works in O(1) because it only changes some pointers and fields.  
Size(): returns the size of the heap from the size field in O(1)

counterRep(): Returns an array of counters/ The Ith entry counts the number of trees of order I . The complexity is O(n).
delete(Heapnode x): deletes the given Heapnode by using the decreaseKey method to make X the minimum node of the heap and then using deleteMin method. The complexity is O(n) in the worst case and O(logn) amortized because the complexity of deleteMin.

decreseKey(Heapnode x, int delta): Decreases the key of the given node by delta. At the end of this method calls cascadigCut method. The complexity is O(h) in worst case because of the worst case of cascading cut but also O(1) amortized.

Cut(): removes a node from its parent and adds it back to the root list of the heap. The method increases the totalCuts and marking the parent of the cut node if he is not a root. The complexity is O(1).

cascadingCut(): cuts up the tree by repeatedly calling the cut() method on a node and its parent,
until a node is encountered that is not marked or until the root of the tree is reached.
This method is used to maintain the heap's min-heap property when a node's key is decreased
or when a node is removed from the heap. If there is a chain of marked nodes the method will take in worst case O(h) h is the height of the tree.

nonMarked(): This method returns the current number of non marked nodes in the tree in O(1).

Potential(): This function returns the current potential of the Heap, 
which is:Potential = #trees + 2*#marked .In words: The potential equals to the number of trees in the Heap plus twice the number of marked nodes in the Heap. This is O(n) in worst case because calling the method numberOfTrees is WC O(n).

totalLinks(): This static function returns the total number of link operations made during the run-time of the program. This is O(1).

totalCuts(): This static function returns the total number of cuts operations made during the run-time of the program. This is O(1).
