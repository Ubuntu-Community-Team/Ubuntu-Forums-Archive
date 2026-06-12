---
title: "help with a script please"
date: 2008-11-30
forum: General Help
---

### Post by TheKrangLegions on 2008-11-30
I been working on this forever can you please show fully how to create these 2 small scripts.  It would be very appreciated! the editor im using is VI





1.   Write a script called simple.sh to do the following:
      
     Displays "There are no arguments"  if no arguments were entered.
     Displays  "There are n arguments"  if arguments were entered where  					n is the number of arguments.
     Displays "The arguments are  a, b, c"  when arguments are entered and a, b, c are agrument1, 	argument2 etc.


     




                                Menu
		
		a.	Current date and time
		b.	Users currently logged in
		c.	Number of users logged in
		d.      Contents of current directory
                
                      Enter Choice..........




2.   Write a shell script to implement the menu above. Call the script menu.sh

Execute the appropriate commands only when the user enters one of the menu choices.  Display an error message such as "invalid choice"  if the choice is not a, b,c, or d.
Remember that the read statement followed by a variable name will obtain input from the user.

Use the case structure to evaluate the choice entered.



1.	Make both scripts executable.
2.	Start the script command with lab8.txt as the file name.
3.	Display the contents of the simple.sh script in 1 above with cat
4.	Display the contens of menu.sh with cat.
5.	Run simple.sh with no arguments
6.	Run simple.sh with three arguments
7.	Run menu.sh four times. first time select choice a, etc.
8.	Run menu.sh and enter choice x

---

### Post by bruce89 on 2008-11-30
I'm afraid getting someone else to do your homework is frowned on. If you need some small hints, perhaps that's not as bad.

Yay, this is my 3,000th post.

---

### Post by cybergalvez on 2008-11-30
> **TheKrangLegions said:**
> I been working on this forever can you please show fully how to create these 2 small scripts.  It would be very appreciated! the editor im using is VI





1.   Write a script called simple.sh to do the following:
      
     Displays "There are no arguments"  if no arguments were entered.
     Displays  "There are n arguments"  if arguments were entered where  					n is the number of arguments.
     Displays "The arguments are  a, b, c"  when arguments are entered and a, b, c are agrument1, 	argument2 etc.


     




                                Menu
		
		a.	Current date and time
		b.	Users currently logged in
		c.	Number of users logged in
		d.      Contents of current directory
                
                      Enter Choice..........




2.   Write a shell script to implement the menu above. Call the script menu.sh

Execute the appropriate commands only when the user enters one of the menu choices.  Display an error message such as "invalid choice"  if the choice is not a, b,c, or d.
Remember that the read statement followed by a variable name will obtain input from the user.

Use the case structure to evaluate the choice entered.



1.	Make both scripts executable.
2.	Start the script command with lab8.txt as the file name.
3.	Display the contents of the simple.sh script in 1 above with cat
4.	Display the contens of menu.sh with cat.
5.	Run simple.sh with no arguments
6.	Run simple.sh with three arguments
7.	Run menu.sh four times. first time select choice a, etc.
8.	Run menu.sh and enter choice x

Does it have to be a bash script? with Python its pretty simple, your arguments are in sys.argv.  You can most likely do everything you need to do importing only os and sys

Jose

---

### Post by TheKrangLegions on 2008-11-30
id just be happy with seeing how to do in VI lines in how they go like 

1: if command blah blah
2:
3:

so I know what im doing

---

### Post by fixitdude on 2008-11-30
When all else fails, use google.

This is close to what you want to do, the first part checks to see if any arguments are entered the rest seems to do other checks that you may find useful.

[http://www.tldp.org/LDP/abs/html/internalvariables.html#ARGLIST](http://www.tldp.org/LDP/abs/html/internalvariables.html#ARGLIST)

What did I search for? "shell scripting"

Some other good resources:
[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
[http://www.tinker.ncsu.edu/LEGO/shell_help.html](http://www.tinker.ncsu.edu/LEGO/shell_help.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

### Post by TheKrangLegions on 2008-11-30
the reason im asking having problems with the commands to work in the construct.  If I had a example like VI style or showing how the lines go im fine.  Just a newbie at this stuff.

---

### Post by TheKrangLegions on 2008-11-30
yea if anyone knows I would so appreciate, just frustrating at times

---

### Post by TheKrangLegions on 2008-12-01
I appreciate everyones help does anyone know?

---

### Post by Diabolis on 2008-12-01
> **TheKrangLegions said:**
> the reason im asking having problems with the commands to work in the construct.  If I had a example like VI style or showing how the lines go im fine.  Just a newbie at this stuff.

Sounds like you think that you must write it in VI, as if it were a programming language. VI is just a text editor, like saying notepad or gedit. As one of the posts above mentioned, what you need to learn is a little bit of **shell scripting**.

Example:
[PHP]#! /bin/sh
echo "This is a shell script"
echo "This is the content of the current directory: "
ls -l
done[/PHP]

Put that code in a file called **example.sh**

Make it executable:
```
chmod +x example.sh
```

Run it:
```
./example.sh
```

---

### Post by TheKrangLegions on 2008-12-01
shoot was trying to hit quick reply, didnt mean to remove thanks, I I do have a thanks if that can be fixed.  

the way im doing it is the way you got as a example.  Do you know how the rest go?

---

### Post by Diabolis on 2008-12-01
This is clearly homework and probably no one in this forums will do it for you. You already have the answers you need, learn shell scripting and linux commands. What you need to learn for this task is not hard at all.

To receive arguments in a shell script you use the variables $1, $2, $3 etc.
Example:
[PHP]#!/bin/sh
Argument1=$1
echo "The first argument is: $Argument1"[/PHP]

Now, if you run this script like this:
```
./example.sh Foo
```

It will print in the screen the following:
```
The first argument is: Foo
```

A good resource for linux commands: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by lavinog on 2008-12-01
> **TheKrangLegions said:**
> 

1.   Write a script called simple.sh to do the following:
      
     Displays "There are no arguments"  if no arguments were entered.
     Displays  "There are n arguments"  if arguments were entered where  					n is the number of arguments.
     Displays "The arguments are  a, b, c"  when arguments are entered and a, b, c are agrument1, 	argument2 etc.


assuming we are talking about bash:

$* will give you all arguments passed to a script
${#VARIABLE} will give you n arguments in VARIABLE





> **TheKrangLegions said:**
> 
                                Menu
		
		a.	Current date and time
		b.	Users currently logged in
		c.	Number of users logged in
		d.      Contents of current directory
                
                      Enter Choice..........




2.   Write a shell script to implement the menu above. Call the script menu.sh

Execute the appropriate commands only when the user enters one of the menu choices.  Display an error message such as "invalid choice"  if the choice is not a, b,c, or d.
Remember that the read statement followed by a variable name will obtain input from the user.

Use the case structure to evaluate the choice entered.

you can use echo to display the menu:
```

echo '                 Menu
		
		a.	Current date and time
		b.	Users currently logged in
		c.	Number of users logged in
		d.      Contents of current directory
                
                      Enter Choice..........'

```
"Remember that the read statement followed by a variable name will obtain input from the user."
```

# dont use dollar sign with read
read choice
# use dollar sign when referencing the variable. Also it is good to use quotes
echo "$choice"
case "$choice" in
...

```
"Use the case structure to evaluate the choice entered."
google "bash case" for the case structure if you don't know it.


> **TheKrangLegions said:**
> 
2.	Start the script command with lab8.txt as the file name.

What class is this?
You do realize that google will be caching this post, and your instructor will be able to find it by just entering in a couple of lines from the assignment.

---

### Post by lavinog on 2008-12-01
google: "Display the contents of the simple.sh script in 1 above with cat"
and you will find this post, and many others.
also I found this:
[http://student.ccbcmd.edu/~arichard/cmsc142/labs/lab8.txt](http://student.ccbcmd.edu/~arichard/cmsc142/labs/lab8.txt)

and if this is a linux/unix class, why is lab7 a word document?
[http://student.ccbcmd.edu/~arichard/cmsc142/labs/lab7.doc](http://student.ccbcmd.edu/~arichard/cmsc142/labs/lab7.doc)

---

### Post by Diabolis on 2008-12-01
:lolflag:

---

### Post by fixitdude on 2008-12-06
Everything is on YouTube!

Amazing, lots of stuff there, I searched "shell scripting tutorial", even a ubuntu specific one was listed.

[http://www.youtube.com/results?search_query=shell+scripting+tutorial](http://www.youtube.com/results?search_query=shell+scripting+tutorial)

Have fun, the only other option is to go to a local school and take a beginning programming course.

YouTube is better, you don't have to drive there, or pay anything, but patience is needed.

Have fun!

---

