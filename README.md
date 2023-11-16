# WEEK-1-Assignment

Debugging is the process of locating and fixing errors (called bugs) in a computer program that can cause it to crash, behave erratically or be susceptible to hacker attack. Objective: To identify and fix errors in a Python program that manipulates strings.

Code 1: def reverse_string(s): 
reversed = "" for i in range(len(s) - 1, -1, -1):
reversed += s[i] return reversed

def main():
  input_string = "Hello, world!" 
  reversed_string = reverse_string(input_string) 
  print(f"Reversed string: {reversed_string}")

if name == "main": main()

# ERRORS:
=>There are no errors in the above program. It is a valid Python code that reverses a string using a for loop and string concatenation . The Error explanation for the code is: The function reverse_string(s) takes a string s as a parameter and returns a new string that is the reverse of s. 
The function initializes an empty string reversed to store the reversed string. The function uses a for loop to iterate over the characters of s in reverse order, from the last index to the first index, using the range function with a negative step of -1. 
The function appends each character of s to the reversed string using the += operator. The function returns the reversed string after the loop ends. The main function calls the reverse_string function with the input string “Hello, world!” and assigns the result to the variable reversed_string. The main function prints the reversed_string using the formatted string literal f"Reversed string: {reversed_string}". The main function is executed only if the file is run as a script, not as a module, by checking the name variable against the string "main".

Code2:
Objective: To identify and fix errors in a Python program that validates user input.

def get_age():
  age = input("Please enter your age: ")
  if age.isnumeric() and age >= 18:
     return int(age) else: return None

def main():
   age = get_age()
   if age: 
     print(f"You are {age} years old and eligible.")
  else: 
     print("Invalid input. You must be at least 18 years old.")

if name == "main": main()

# ERRORS:

● The error is in the line if age.isnumeric() and age >= 18:. This line will raise a TypeError exception because you are trying to compare a string (age) with an integer (18). You should convert age to an integer before comparing it with 18, or use the int() function inside the isnumeric() method, like this: if age.isnumeric() and int(age) >= 18:.
● The suggestion is to use a loop to ask the user for their age until they enter a valid input, instead of returning None and ending the program. You can use a while loop with a break statement, like this:

# CORRECT CODE:

def get_age(): 
while True: 
    age = input("Please enter your age: ")
    if age.isnumeric() and int(age) >= 18: 
        return int(age) 
    else:
        print("Invalid input. You must be at least 18 years old.")

Objective:
To identify and fix errors in a Python program that reads and writes to a file. 
Code3: 
def read_and_write_file(filename):
try: 
  with open(filename, 'r') as file:
  content = file.read() with open(filename, 'w') as
file: 
  file.write(content.upper()) 
  print(f"File '{filename}' processed successfully.") 
except Exception as e:
   print(f"An error occurred: {str(e)}")

def main():
 filename = "sample.txt" read_and_write_file(filename)

if name == "main": 
      main()

# The errors and suggestions are:
● You used ‘r’ mode to open the file for reading, and then ‘w’ mode to open the same file for writing. This will erase the original content of the file before you can read it. You should use ‘r+’ mode instead, which allows you to read and write the same file without erasing it.
● You did not seek to the beginning of the file before writing the content in uppercase. This will append the uppercase content to the end of the file, instead of replacing the original content. You should use file.seek(0) to move the file pointer to the beginning of the file before writing. 
● You did not truncate the remaining content of the file after writing the uppercase content. This will leave some lowercase content at the end of the file, if the original content was longer than the uppercase content. You should use file.truncate() to remove any content after the current file pointer.

# CORRECT CODE:

A function to read and write a file in uppercase def read_and_write_file(filename): try: # Use 'r+' mode to read and write the same file with open(filename, 'r+') as file: content = file.read() # Seek to the beginning of the file file.seek(0) # Write the content in uppercase file.write(content.upper()) # Truncate any remaining content file.truncate() print(f"File '{filename}' processed successfully.") except Exception as e: print(f"An error occurred: {str(e)}")

def main(): filename = "sample.txt" read_and_write_file(filename)

if name == "main": main()

submit the corrected code with comments explaining the issues they found and the solutions they implemented.

(next page) Code4: def merge_sort(arr): if len(arr) <= 1: return arr

mid = len(arr) // 2
left = arr[:mid]
right = arr[mid:]

merge_sort(left)
merge_sort(right)

i = j = k = 0

while i < len(left) and j < len(right):
    if left[i] < right[j]:
        arr[k] = left[i]
        i += 1
    else:
        arr[k] = right[j]
        j += 1
    k += 1

while i < len(left):
    arr[k] = left[i]
    i += 1
    k += 1

while j < len(right):
    arr[k] = right[j]
    j += 1
    k += 1
arr = [38, 27, 43, 3, 9, 82, 10] 
merge_sort(arr) print(f"The sorted array is: {arr}")

The code aims to implement the merge sort algorithm. However, there is a bug in the code. When the student runs this code, it will raise an error or produce incorrect output. The student's task is to identify and correct the bug.

Hint: Pay close attention to the recursive calls and the merging step.

# ERRORS AND EXPLANATION:
● The error is in the line merge_sort(left) and merge_sort(right). These lines are missing the return statement, which means that the recursive calls will not return the sorted subarrays to the parent call. You should add the return statement to these lines, like this: left = merge_sort(left) and right = merge_sort(right). 
● The suggestion is to use the += operator to simplify the code and avoid using the index variable k. You can append the elements of the subarrays to the main array using the += operator, like this: arr += left[i:] and arr += right[j:].

# CORRECT CODE:

A function to implement the merge sort algorithm
def merge_sort(arr): if len(arr) <= 1: return arr

mid = len(arr) // 2
left = arr[:mid]
right = arr[mid:]

# Use the return statement to get the sorted subarrays
left = merge_sort(left)
right = merge_sort(right)

i = j = 0
# Clear the main array
arr.clear()

while i < len(left) and j < len(right):
    if left[i] < right[j]:
        arr.append(left[i])
        i += 1
    else:
        arr.append(right[j])
        j += 1

# Use the += operator to append the remaining elements
arr += left[i:]
arr += right[j:]

return arr
arr = [38, 27, 43, 3, 9, 82, 10] merge_sort(arr) print(f"The sorted array is: {arr}")

The output for the above program is: The sorted array is: [3, 9, 10, 27, 38, 43, 82]





# ASSIGNMENT  2:

# Grocery-inventory-management
An inventory management system (or inventory system) is the process by which you track your goods throughout your entire supply chain, from purchasing to production to end sales. It governs how you approach inventory management for your business.

Define a variable to store the inventory data as a dictionary
inventory = {}

Define a function to add new items to the inventory
def add_items():
# Ask the user how many items they want to add 
n = int(input(“How many items do you want to add? “)) 
# Use a for loop to iterate n times
for i in range(n):
# Ask the user the name and quantity of the item 
name = input(“Enter the name of the item: “)
quantity = int(input(“Enter the quantity of the item: “)) 
# Update the inventory with the item and quantity
inventory.update({name: quantity}) 
# Print a confirmation message 
print(f”Added {quantity} {name}(s) to the inventory.”)

Define a function to update existing items’ quantities
def update_items():
# Ask the user how many items they want to update
n = int(input(“How many items do you want to update? “))
# Use a for loop to iterate n times for i in range(n):
# Ask the user the name and quantity of the item 
name = input(“Enter the name of the item: “) 
quantity = int(input(“Enter the quantity to add or subtract: “)) 
# Check if the item exists in the inventory if name in inventory:
# Update the inventory with the new quantity 
inventory[name] += quantity
# Print a confirmation message
print(f”Updated {name} quantity to {inventory[name]}.”)
else:
# Print an error message
print(f”{name} does not exist in the inventory.”)

Define a function to view the current inventory
def view_items():
# Print a header message
print(“The current inventory is:”)
# Use a for loop to iterate over the items and quantities in the inventory for item,
quantity in inventory.items(): 
# Print the item and quantity print(item, quantity)

Define a function to remove items from the inventory
def remove_items():
# Ask the user how many items they want to remove
n = int(input(“How many items do you want to remove? “)) 
# Use a for loop to iterate n times for i in range(n): 
# Ask the user the name of the item 
name = input(“Enter the name of the item: “) 
# Check if the item exists in the inventory if name in inventory:
# Remove the item from the inventory and store the quantity
quantity = inventory.pop(name)
# Print a confirmation message 
print(f”Removed {quantity} {name}(s) from the inventory.”) 
else:
# Print an error message print(f”{name} does not exist in the inventory.”)

Define a function to display the menu options
def display_menu():
# Print a welcome message
print(“Welcome to the Grocery Store Inventory Management Program.”) 
# Print the menu options
print(“Please choose one of the following options:”) 
print(“1. Add new items to the inventory.”) 
print(“2. Update existing items’ quantities.”) 
print(“3. View the current inventory.”) 
print(“4. Remove items from the inventory.”)
print(“5. Exit the program.”)

Define a variable to store the user’s choice
choice = 0

Use a while loop to repeat until the user chooses to exit
while choice != 5: 
# Display the menu display_menu() 
# Ask the user to enter their choice
choice = int(input(“Enter your choice: “))
# Use conditional statements to execute the corresponding function 
if choice == 1:
# Call the add_items function add_items() 
elif choice == 2:
# Call the update_items function update_items() 
elif choice == 3:
# Call the view_items function view_items()
elif choice == 4:
# Call the remove_items function remove_items()
elif choice == 5: 
# Print a farewell message 
print(“Thank you for using the program. Goodbye.”)
else:
# Print an invalid message 
print(“Invalid choice. Please try again.”)

OUTPUT:
Welcome to the Grocery Store Inventory Management Program. Please choose one of the following options:

1.Add new items to the inventory.
2.Update existing items’ quantities.
3.View the current inventory.
4.Remove items from the inventory.
5.Exit the program. 
Enter your choice: 1 
How many items do you want to add? 2
Enter the name of the item: milk
Enter the quantity of the item: 20 
Added 20 milk(s) to the inventory.
Enter the name of the item: bread 
Enter the quantity of the item: 15
Added 15 bread(s) to the inventory.
Please choose one of the following options:
1.Add new items to the inventory.
2.Update existing items’ quantities.
3.View the current inventory.
4.Remove items from the inventory.
5.Exit the program.
Enter your choice: 3 
The current inventory is: milk 
20 bread 15
Please choose one of the following options:
1.Add new items to the inventory.
2.Update existing items’ quantities.
3.View the current inventory.
4.Remove items from the inventory.
5.Exit the program.
Enter your choice: 2
How many items do you want to update? 1 
Enter the name of the item: milk
Enter the quantity to add or subtract: -5 
Updated milk quantity to 15. 
Please choose one of the following options:
1.Add new items to the inventory.
2.Update existing items’ quantities.
3.View the current inventory.
4.Remove items from the inventory.
5.Exit the program.
Enter your choice: 4
How many items do you want to remove? 1
Enter the name of the item: bread 
Removed 15 bread(s) from the inventory. 
1.Please choose one of the following options:
2.Add new items to the inventory.
3.Update existing items’ quantities.
4.View the current inventory.
5.Remove items from the inventory.
Exit the program. Enter your choice: 5
