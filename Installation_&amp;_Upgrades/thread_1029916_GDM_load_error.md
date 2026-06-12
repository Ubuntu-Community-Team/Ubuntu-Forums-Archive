---
title: "GDM load error"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Nucy on 2009-01-03
Hey i am litterally brand new to any type of linux Ubuntu OS so it might very well be something im doing wrong but i loaded up Ubuntu 8.10 after partioning my HD loaded works good when i reboot my computer i get to the dual boot Windows Vista or Ubuntu boot Ubuntu it loads than gives me a command line ive typed startx, sudo startx, gdm, sudo gdm, all that stuff and at some point it gives me a gdm already running error and than a cant find screens error... so i can see any desktop...


now is this maybe because i am using an HDMI cable hooked up to my TV for a monitor and the drivers arent installed for Ubuntu to display anything? or am i jus not typing in the right command to load the GUI?!!?!?!?

---

### Post by Nucy on 2009-01-04
Also, it says there is an error in one of the lines of a config.c or something... ill go checkl what it says then come post it here

Ok it comes up with this error, "gdm [8974]: WARNING:
                                 GDM file gdm-daemon-config.c: Line 2033 (): cannot run seteuid to 0:"

---

### Post by Nucy on 2009-01-05
bump...

I've google'd it and no dice, i dont know how to go around anything cause i am infact completley new to all this other than like playin around in ms-dos which doesnt even share to many commands

---

### Post by Rithmarin on 2009-01-05
Have you tried running ubuntu from the live CD? That will give you a good idea if it will work easily out the box on your computer.

What video card does your computer use?

If its a driver support, getting the latest updates may help sort it out. 
run "sudo apt-get update && sudo apt-get upgrade" to get them.

---

### Post by Nucy on 2009-01-06
Im running an ATI radeon 3600, and thank you i will try updating the drivers and edit this post if it works or not

---

### Post by Nucy on 2009-01-06
I ran those commands and it went through all the paces to doit got right to the end and said cant write to disk no space on device or something like that... i dunno what its installing because i have 348 gig on the partition with Ubuntu on it, and i doubt that that isnt enough

---

### Post by Rithmarin on 2009-01-06
"df" will tell you what file systems are mounted and how much space, heres part of mine as an example: 
rith@ub2:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/ub2-root  51606140  13721004  35263696  29% /
/dev/sda2               482246     41360    415986  10% /boot
rith@ub2:~$

---

### Post by Nucy on 2009-01-09
it told me i have 1% or 0% used in most of the areas, but when i update and upgrade it tries to write to E: drive, which is my disk drive, im not running off the disk i also dont have a disk in there so is there a way to change that?

---

### Post by Nucy on 2009-01-11
as i said absolute beginner, ive been looking for tutorials but not much is helping

---

### Post by Rithmarin on 2009-01-12
E drive makes it sound like you are using the installation method where it installs within a windows partition.  Is that right, or is it on its own partition? 

Can you post the output to the df command here? From what you've said I'd expect to see a reference to E: in the filesystem column. If thats your cd drive, we will probably need to change its location.

---

