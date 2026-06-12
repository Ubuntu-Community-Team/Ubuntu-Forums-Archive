---
title: "I cant update or install things, Help Please!"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by Psyco_Chipmunk on 2008-12-15
I did something awhile back that made it so I cant update or use the Add/Remove or synaptic package manager.  I don't remember what I did, it was something complicated and I didn't really know what I was doing.  anyways, when I try to open Add/Remove, synaptic or update manager they start to open then close after a few seconds.  Is there a way to fix this?

---

### Post by frankleeee on 2008-12-15
try running this command in the terminal
sudo dpkg --configure -a
then run
sudo apt-get install -f
then 
sudo apt-get update
then 
sudo apt-get upgrade
each command that is if no errors occur.

---

### Post by randywilharm on 2008-12-15
you may want to check this out:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10-p3](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10-p3)

---

### Post by Psyco_Chipmunk on 2008-12-15
Well, the problem is, I cant apt-get anything.  For example, I try to get opera.  

laptop:~$ sudo apt-get install opera
Segmentation faultsts... 77%
luke@luke-laptop:~$ 
  Thats what happens.

---

### Post by frankleeee on 2008-12-15
Okay did you try the commands in the order I listed them. Also do you get a error message if you try and open synaptic or add remove. the commands generally fix the problem your describing don't associate them not working with the apt command.

---

### Post by Psyco_Chipmunk on 2008-12-15
I cant do the commands you told me, this happens when I do the second command.  

 sudo apt-get install -f
Segmentation faultsts... 76%

---

### Post by frankleeee on 2008-12-15
Since I am not a geek this segmentation error or whatever it is makes no sense to me. Do you get a error message on trying to open synaptic or add remove. I think your apt source list was corrupted by having add remove open and running a synaptic command or a terminal download. None of these can be open together when accessing the apt source repositories for a download do you think this is the case and do you understand what I am talking about.

---

### Post by Psyco_Chipmunk on 2008-12-15
I understand what your saying but thats not the problem.  No error messages come up, when I open them, they just start up like usual but then exit off after about 3-5 seconds.

---

### Post by frankleeee on 2008-12-15
Have you looked in software sources in system administration to see if the CD on the first tab is off, and have you added anything in the past to the apt source list. Can you run this in the terminal and post it.
cat /etc/apt/sources.list
Since you don't remember what you were doing when you stopped being able to access synaptic or add remove all I can do with my limited knowledge is follow the paths I do that wont bork the system. I ran into a similar problem a couple of days ago when I tried to add the medibuntu repos while add remove was installing, I fixed it by just running the medibuntu install again but I still had a corrupted apt source associated with the medibuntu. Does this using the terminal or add remove or synaptic at the same time jog your memory.Also if you just put synaptic in the terminal does it open.

---

### Post by nmz787 on 2008-12-15
try placing strace in front of apt-get

---

