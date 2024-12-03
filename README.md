# module9.py
# Oluwapelumi Omidiji
# 11/24/2024

def problem1():
    """
    This function creates an infinite while loop that will continuously print
    the message "This will run forever" until manually interrupted.
    The loop will not stop unless an external action (such as Ctrl+C) is performed.
    """
    while True:
        print("This will run forever")

# WARNING: Calling this function will cause the program to run indefinitely.
# To stop it, you will need to interrupt the process manually.
def problem2():
    """
    This function initializes a list and uses a while loop to append the numbers
    from 0 to 10 to the list. Once the loop finishes, it prints the list of numbers.
    """
    # Step 1: Initialize the list and counter
    L = []  # List to store numbers
    counter = 0  # Starting counter

    # Step 2: Set up the while loop to run until the counter reaches 10
    while counter <= 10:
        # Step 3: Append the current value of the counter to the list
        L.append(counter)
        # Step 4: Increment the counter
        counter += 1

    # Step 5: Print the list containing numbers from 0 to 10
    print(L)

# Example call to test
problem2()
def problem3():
    """
    This function repeatedly asks the user to enter a number and adds the number
    to a list. It keeps a running total of the sum and stops when the total exceeds 100.
    If an invalid number is entered, an error message is shown.
    """
    numbers = []  # List to store the numbers entered by the user
    total = 0  # Initialize the total sum

    # Step 1: Keep requesting numbers until the total sum exceeds 100
    while total <= 100:
        user_input = input("Please enter a number: ")
        try:
            # Step 2: Try converting the user input to a float and add to total
            number = float(user_input)
            numbers.append(number)  # Add the number to the list
            total += number  # Add the number to the running total
        except ValueError:
            # Step 3: Handle invalid input (non-numeric input)
            print("Invalid input. Please enter a valid number.")
    
    # Step 4: Print the numbers entered and the total sum
    print("The numbers entered are:", numbers)
    print("The total sum is:", total)

# Example call to test
problem3()
def problem4():
    """
    This function finds all numbers from 0 to 50 that are divisible by 10.
    These numbers are added to a list, which is printed once the loop is completed.
    """
    # Initialize the counter and the list
    counter = 0
    tens = []  # List to store numbers divisible by 10

    # Step 1: Use a while loop to run until the counter reaches 50
    while counter <= 50:
        # Step 2: Check if the counter is divisible by 10
        if counter % 10 == 0:
            tens.append(counter)  # Add to the list if divisible by 10
        # Increment the counter
        counter += 1

    # Step 3: Print the list of numbers divisible by 10
    print("Numbers divisible by 10:", tens)

# Example call to test
problem4()
from typing import Optional

class TreeNode:
    """
    A class representing a node in a binary tree. Each node has:
    - A value (val),
    - A left child (left),
    - A right child (right).
    """
    def __init__(self, val=0, left=None, right=None):
        """
        Initializes a new binary tree node with a given value, left and right child nodes.
        
        Parameters:
        val (int): The value of the node.
        left (TreeNode): The left child node.
        right (TreeNode): The right child node.
        """
        self.val = val
        self.left = left
        self.right = right

class Solution:
    """
    A class to check if a binary tree is symmetric.
    """
    def isMirror(self, left: Optional[TreeNode], right: Optional[TreeNode]) -> bool:
        """
        Helper function to compare two subtrees for mirror symmetry.
        
        Parameters:
        left (TreeNode): The left subtree.
        right (TreeNode): The right subtree.
        
        Returns:
        bool: True if the two subtrees are mirror images, False otherwise.
        """
        stack = [(left, right)]  # Stack to store pairs of nodes for comparison

        while stack:
            left_node, right_node = stack.pop()

            # Both nodes are None, continue to next pair
            if not left_node and not right_node:
                continue
            
            # One of the nodes is None, trees are not symmetric
            if not left_node or not right_node:
                return False
            
            # Values must be equal for symmetry
            if left_node.val != right_node.val:
                return False
            
            # Push the children in the stack for comparison
            stack.append((left_node.left, right_node.right))
            stack.append((left_node.right, right_node.left))

        return True 

    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        """
        Checks if the binary tree is symmetric around its center.
        
        Parameters:
        root (TreeNode): The root of the binary tree.
        
        Returns:
        bool: True if the tree is symmetric, False otherwise.
        """
        if not root:
            return True  # An empty tree is symmetric
        return self.isMirror(root.left, root.right)

# Example usage
if __name__ == "__main__":
    # Create a symmetric tree
    root = TreeNode(1)
    root.left = TreeNode(2)
    root.right = TreeNode(2)
    root.left.left = TreeNode(3)
    root.left.right = TreeNode(4)
    root.right.left = TreeNode(4)
    root.right.right = TreeNode(3)

    # Check if the tree is symmetric
    solution = Solution()  # Create an instance of the Solution class
    print(solution.isSymmetric(root))  # Output: True
