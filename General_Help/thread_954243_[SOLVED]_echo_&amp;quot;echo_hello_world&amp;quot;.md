---
title: "[SOLVED] echo &amp;quot;echo hello world&amp;quot; | at now"
date: 2008-10-21
forum: General Help
---

### Post by sulekha on 2008-10-21
Hi ,

I gave the following command echo** "echo hello world" | at now** at tyhe terminal to test whether echo command is working, to get the o/p

warning: commands will be executed using /bin/sh
job 12 at Tue Oct 21 10:52:00 2008

but the echo command didn't execute

i edited /etc/at.deny file to remove the line bin

 what should i do to make at command working ?

N.B:- I use ubuntu 8.04.1

---

### Post by p_quarles on 2008-10-21
Well, at is kind of weird utility that works differently than people would expect. Two things to understand:

1) The at command runs in a separate terminal, not the one you entered the command into. 

2) The at command pipes stdout into stdin at the time set in the command. In other words, you need to a command that produces stdout, like echo. For example:

```
date > /home/$USER/now.text | at sometime
```
will fail. It first redirects the output of date to a file called now.text and then pipes that file into at's terminal at the time specified. Just like if you typed the current time into your own terminal, you get a command not found error.

If, on the other hand, you run this:
```
echo "date > /home/$USER/now.text" | at sometime
```
you are piping the output of the echo command to the at command, which will work correctly: it will produce a file containing the date and time specified in the second command. 

So, to do what you are attempting, you need to add two things. One, you need to use "wall" (or similar) to make sure the message is sent to *your* terminal. Second, you need another "echo" command. So, the correct version looks like this:
```
echo 'echo "hello world" | wall' | at now
```
This will send the message "hello world" to all logged in users. :)

---

