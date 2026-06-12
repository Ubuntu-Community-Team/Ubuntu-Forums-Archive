---
title: "Help booting Matlab"
date: 2008-10-07
forum: General Help
---

### Post by Borkov on 2008-10-07
Sup UF, 

I got a problem, big enough for me to actually create an account here hah. But it's about Matlab r2008a, I got this software, install it, it runs but after I click out and want to boot up the program again, I can't find a way of doing it, I've tried several ways to boot the program using the terminal, and I even searched for a boot shortcut, but to no avail. So is there a command I can use or even a way to create a shortcut to get this program to run again (I know it runs for sure)

tl;dr: I need a way to boot matlab because I can't find a way to do it myself

---

### Post by matthewbpt on 2008-10-07
Go into the directory you installed matlab in, then go to the bin folder, then double click 'matlab' and select run in terminal... voila matlab runs

---

### Post by iponeverything on 2008-10-07
right click on your desktop and go the second option "Create Launcher"
Fill in the fields

Name =       Matlab
Command =    matlab

click on "ok"

you will then have an icon on the desktop for it.

---

### Post by kramulous on 2008-10-07
Or, you can open a terminal and just type:

```
matlab
```

in the directory that you want as the Current Working Directory.

---

### Post by Borkov on 2008-10-08
> **kramulous said:**
> Or, you can open a terminal and just type:

```
matlab
```

in the directory that you want as the Current Working Directory.


Tried it, didn't work. 

I tried booting it from the bin and it wouldn't boot from there and not even when I ran it from the terminal that way. 

I know this damn thing works, I just need to figure out how to get it up....

---

### Post by kramulous on 2008-10-08
Where is your Matlab install directory?

Mine, for example, is in

```
/home/kramulous/Software/MatlabR2008a
```

So, in my /home/kramulous/.profile, I have added:

```
# Setup Matlab
PATH=/home/kramulous/Software/MatlabR2008a/bin:$PATH
export PATH
```

What errors do you get?

---

### Post by Borkov on 2008-10-12
> **kramulous said:**
> Where is your Matlab install directory?

Mine, for example, is in

```
/home/kramulous/Software/MatlabR2008a
```

So, in my /home/kramulous/.profile, I have added:

```
# Setup Matlab
PATH=/home/kramulous/Software/MatlabR2008a/bin:$PATH
export PATH
```

What errors do you get?

Mine is in /home/borkov/matlab

But I ran it in the terminal and it boots up but it won't perform anything, not even 1+1. I had to reinstall this sucker to get at least this far, what do you think maybe wrong with it

---

