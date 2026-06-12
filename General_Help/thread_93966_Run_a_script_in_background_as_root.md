---
title: "Run a script in background as root?"
date: 2005-11-23
forum: General Help
---

### Post by Global Havok on 2005-11-23
I have written a battery monitor script in perl as no power managers seem to work correctly on my vaio laptop.  Anyways, it all works great until I call my hibernate script (which must be run as root).

My question is this:  How can I get my script to load into the background with root privleges?

---

### Post by robotgeek on 2005-11-23
running the script with sudo ./script will run it as root

---

### Post by Global Havok on 2005-11-23
Problem is, i want the script to load automatically when i log in, not prompt me for the password.  I'm trying to avoid manually starting the script everytime I log in.  Is this possible?

---

### Post by 23meg on 2005-11-23
Put it into /etc/init.d , make it executable and create a symlink to it in /etc/rcX.d , X being the runlevel it will start in. AFAIK runlevels 2-5 in Ubuntu are essentially the same so it could be any of them.

---

### Post by odin on 2005-11-23
[QUOTE=23meg]Put it into /etc/init.d , make it executable and create a symlink to it in /etc/rcX.d , X being the runlevel it will start in. AFAIK runlevels 2-5 in Ubuntu are essentially the same so it could be any of them.[/QUOTE]


uff you dont know how easy you have made my life with 3 lines!!!

Thank's :D

---

### Post by 23meg on 2005-11-23
You're welcome. Those interested in runlevels tweaking should also take a look at [Boot-Up Manager]("http://ubuntuforums.org/forumdisplay.php?f=75").

---

### Post by Granduke on 2005-12-28
There are only two steps in this process and I don't know how to do either.
Can someone please tell me:
How to make a script executable and
How to create a symlink

thanks.

---

### Post by Zwack on 2005-12-29
To make a script executable...

chmod a+x <script_name>

e.g. chmod a+x dummyscript

To make a symbolic link

ln -s <script name> <location and name of symbolic link>

e.g. ln -s /etc/init.d/dummyscript /etc/rc2.d/S15dummyscript

btw the Symbolic links should be named SxxNAME or KxxNAME where S is for start scripts, K is for kill scripts and xx is the order in which it will be run.

Z.

---

### Post by Granduke on 2005-12-29
Thanks Zwack.

---

### Post by Zwack on 2005-12-29
No Problem...

I've sat through enough classes covering the init sequence that I should know it by now... :-)

Z.

---

