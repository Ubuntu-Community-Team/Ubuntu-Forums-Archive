---
title: "Bash Script Issue"
date: 2008-08-01
forum: General Help
---

### Post by thestig_992 on 2008-08-01
Ive been writing a script recently to automatically run transmission at certain times, and am having one issue with running terminal commands through it (don't know the proper term for doing this, soz..XD)

When i type the following into a terminal session, it runs transmission without interrupting my current session...
```
transmission &
```
That works fine, and is exactly what i want in my script. But...when I have the line
```
`transmission &`
```
in the script, it runs as though I never used an & at all. So far Ive tried \& also, but nothing i can think of works...
So my question is: does anyone know a way of running a terminal command from a script without interrupting the session?

---

### Post by northern lights on 2008-08-01
Why exactly do you need a shell script in the first place?

Is there a particular reason you wouldn't simply use cron?

---

### Post by thestig_992 on 2008-08-01
I use cron.hourly to run it
The reason i need a script is because it does more than open transmission, it open new files and moves them and so on...

---

### Post by justleen on 2008-08-01
Considering you launch this from cron... why do you need a "&" ?
its already in the background..
so just use `transmission`
im guessing you dont even need the ``, since that will allow for variable assignment and I cant imagine why you'd want ```
 $STRING=`transmission`
``` since that with give you a var with the output of transmission in it..

when you need to run this script by hand, then add the &
```
 ./myscript.sh & 
```

---

### Post by thestig_992 on 2008-08-01
Im not sure if this makes a difference, but when i run the script without using cron (as in "sh ./script.sh"), this is where i have my problem
since im running it through a terminal, i get feedback on what the script is doing. To test if the & was the problem, i wrote a short script that was meant to run transmission then quit it
```
#!/bin/bash

`transmission &`
echo "text"
`transmission -q`
```
but, the terminal window locks up on "transmission &" until i tell the gui transmisison that pops up to quit, then runs the next lines.

What I need to know is if there is a way to make the script run all the way through without any need of manually closing transmission

---

### Post by c2olen on 2008-08-01
Ok,

The ` arent necessary at all in this scenario.
```
transmission &
``` doesn't lock my terminal and ```
`transmission &` 
```does. The & is interpreted literally here, and not as a background indicator.

Even though I still can't figure out the use of this script, it should till work without the `` .

---

### Post by thestig_992 on 2008-08-01
thanks works now...
I dont know where, but i thought i read that the ` were required to input something into a terminal...shows you what a noob i am to scripting...

---

### Post by c2olen on 2008-08-01
> **thestig_992 said:**
> ...shows you what a noob i am to scripting...

Your welcome.
We all had to start somewhere at some point, so we were all noobs once.

---

### Post by caljohnsmith on 2008-08-01
Thestig_992, in case you are curious, the single backquotes ` ` are used typically when you want to set a variable equal to the result of some executed program:
```
john@TECH5321:~$ myvar="uname -r"
john@TECH5321:~$ echo $myvar
uname -r
john@TECH5321:~$ myvar=`uname -r`
john@TECH5321:~$ echo $myvar
2.6.24-20-rt
```
Note in the first case myvar is set as literally the string "uname -r", but in the second case myvar is set to the result returned when executing "uname -r".

Another good use for them is when executing a command, and you give it an argument that is the result of executing another command (sorry if that sounds convoluted, see example):
```

john@TECH5321:~$ cd /lib/modules/`uname -r`
john@TECH5321:/lib/modules/2.6.24-20-rt$ 

```
Note that I changed my directory to /lib/modules/2.6.24-20-rt by using `uname -r` to find the kernel I'm currently using.

---

