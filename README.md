# useful-regex

### Here I list some regular expressions (regex) which I find useful when working with large amounts of text. If you've ever had to do something tedious like add something to the start of every sentence in a file that contains hundreds of sentences, you've probably come to the right place. I hope these are useful to you!

##### WARNING! SOME OF THESE ARE VERY POWERFUL AND CAN GIVE UNEXPECTED RESULTS! REMEMBER TO BACK UP YOUR DOCUMENTS BEFORE USING THESE REGEX COMMANDS. I CANNOT BE HELD RESPONSIBLE FOR ANY DAMAGE CAUSED.


## Find start and end of sentences

#### End of sentence
	$ // end of sentence
	k$ // ends with -k
	$ing // ends with -ing 
You can use this to do things like replace all words that end with -ing to -ed. For example: **Working** -> *Worked*, **Turning** -> *Turned*, **Doing** -> *Doed*..?

#### Start of sentence
	^ // start of sentence
	^e // starts with -e
	^car // starts with -car
Similar to end of sentence. You can use this ^ to add things to the start of a sentence, such as to wrap things in double quotes.
##### Example: Find all integers in your code and turn them into doubles
Imagine you have this
> int a = 21341
int b = 8398913

You want to change the **int** to **Double**, and append .05 to the end of each number. What do you do?
	
	Find: ^int ([a-z]+ = [0-9]+)
	Replace: Double \1.05
Result: 
> Double a = 21341.05
Double b = 8398913.05

Explanation: **^int** matches the first few characters, which is int followed by a space. Then we have an **open parentheses**, which starts our capture group. This capture group stores the part in the parentheses so we can use it later. **[a-z]+** matches one or more characters from a to z (we are assuming our variables don't have symbols in them for brevity). Then we have **some spaces and an equals sign** as we see in the code. Finally we have **[0-9]+** followed by a **closing parentheses** bracket, indicating we are looking for one or more number at the end. 

This regex basically reads as: **Find a sentence that starts with int, then has a space in front, and then some letters, space, an equal sign, space, and then some numbers.** 

We put everything after the int in a capture group, so that we can refer to it with \1. In replace, we type in Double, then the capture group \1 (everything in the brackets gets pasted there), then a .05 to append the .05 we wanted to append in the beginning.

***
