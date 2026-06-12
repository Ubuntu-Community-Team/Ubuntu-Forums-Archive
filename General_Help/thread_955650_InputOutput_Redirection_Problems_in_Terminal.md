---
title: "Input/Output Redirection Problems in Terminal"
date: 2008-10-22
forum: General Help
---

### Post by Lindrick on 2008-10-22
Hi, i'm very new to Ubuntu, and linux in general, but i'm very keen to learn, i've begun doing some work in terminal within KDE, but i'm now stuck. What i'm trying to do is redirect the output produced from a command in terminal into a .txt file. i'm trying to produce a listing of a specific directory, as well as all the sub-directories and files within that directory. any help would be GREATLY appreciated! as would a link to the most useful commands within terminal, i have found i can redirect the output of the directory i am currently in but after that i'm lost. I'm used to MS-DOS and command prompt so i know i have the right idea in principle as i can perform these tasks in Windows. any advice the sooner the better would be greatly appreciated as it's driving me crazy not being able to figure it out! :confused:
 
Thanks in advance!

---

### Post by mschutte on 2008-10-22
I am assuming that you have tried something similar to ***ls -s > somefile.txt*** inside the directory?

You can try to list the contents of the entire directory by using the absolute path name. Example: ***ls -la -R /home/username > somefile.txt***

Hopefully that will be what you are looking for??

---

### Post by ibuclaw on 2008-10-22
There are three types of redirection in Linux:
[LIST]
[*]**0** - *STDIN* - Keyboard input
[*]**1** - *STDOUT* - Console Output
[*]**2** - *STDERR* - Console Error Output
[/LIST]
To redirect application output to a text file, you only need to be familiar with the latter two.

The numbers above represent their redirection number in the bash shell.
By default, the output that is redirected is is stdout, but you can tell the shell which form of output you which to redirect using these numbers.
So ie: you wish to redirect all stderr to a textfile. You would do this with the following.
```
./appname 2> textfile.txt
```
Or, if you wish to catch both stdout AND stderr, then you would redirect all stderr to stdout.
```
./appname 2>&1 > textfile.txt
```

Hope that clears most things.

Regards
Iain

---

