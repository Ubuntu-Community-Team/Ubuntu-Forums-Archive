---
title: "[SOLVED] teething trouble"
date: 2008-11-17
forum: General Help
---

### Post by Bigneil on 2008-11-17
I'm relatively new to Linux. I would Agree that Ubuntu is easy to install and operate and does most of the jobs i would like it too. BUT..... There always seems to be a wee glitch here and a wee problem there.  Just when you think you got it all working your printer spits out a ream of paper instaed of a nicely printed document, or the Wireless card won't work on your laptop, or your wife has a tizzy because the nice uploader tool for bebo is not working, or you can't use it to add and remove mp3's from your player. or you can't find the program you want in 'add/remove' or 'synaptic', or yuor computer freezes for no apparent reason other that it has been switched on for a few hours.

I know that these sort of problems are probably fixable. but to the average novice who has never studied computing they are very time consuming and annoying.

I love the idea if holding my finger aloft in defiance of microsoft but i have to say that XP is a superior operating system for the novice because when you switch it on, there are no niggles or wee teething problem. the printer works and they wireless picks up.



RANT OVER**

can any one tell me of a program that can make a bootable disk

---

### Post by Het Irv on 2008-11-17
Err.. Bootable disk like from an .iso?

Brasero works pretty well and it is installed by default (Applications -> Sound and Video).


And stick with it, I know how you feel.  Sometimes it seems like nothing wants to work for Linux. I have had those days, even weeks like that.

---

### Post by kestrel1 on 2008-11-17
I find K3B to be far better than Brasero, easy enough to install:
```
sudo apt-get install k3b
```

---

### Post by Coreigh on 2008-11-17
Windows is a pain to learn for a novice Windows user too. Not to mention all the other silly restrictions, like having to pay for software.

Bootable disk like LiveCD, thumbdrive or floppy, ... or what do you need?

---

### Post by Bigneil on 2008-11-17
I'm glad im not the only one. these sort of niggles are fixable but i am a busy person and it takes time to learn about each bit and have 42 failed attempts at it before i get it right.

Yes i would like to make an ISO file then burn it to a disk. i know i have done this in the past when i made my Fiesty disk using infra recorder in xp.

Basically i want a dual boot but i have never owned a xp disk, i borrowed a rip off copy from some one once. but i would like to create my own. I have downloaded it via file share, but don't really know what to do next, presumably turn it into a bootable disk. if i can get past that, then i can create my dual boot and thus avoid the complicated job of trying to find a way of running Sonicstage for my sony walkman in ubuntu. 

If i can't figure it out i'll just buy a ligit copy.  but.... i would prefer to learn to to it myself.

---

### Post by Bigneil on 2008-11-17
I looked at brassero and k3b they are both nice but i liked the look and feel of k3b.     

And yes you are right windows is a pain for new users too.  i was just feeling a bit fed up with glitches and gremlins.  

I also cant get the printer to work  ........  MURMPH
Oh and my pc just randomly freezes for no apparent reason.

would it help to re-install my ubuntu???

---

### Post by kestrel1 on 2008-11-18
If your machine freezes for no reason it could be a hardware fault as well as a software one. You could boot from the live CD & see if you get any problems then. If not then re-install, but if you do I would suggest you look at the CPU temperature.
What printer do you have?

---

### Post by Bigneil on 2008-11-18
I have an epson stylus d92.    i have done a re-install Dual. xp/heron no problems so far,   just that i need a little help with the default operating system.

At the moment i would like xp as default, at least until my wife realizes that all the cool programs she was used to no longer exist on our pc unless we go out and spend a lot of money. lol

i read up on dual boot, and decided that xp then ubuntu, was easier than Ububntu then xp.

so,.... i have istalled xp then installed hardy heron from scratch. but i don't know how to change the default to xp and give myself 30 seconds to decide??......Yes, i'm that slow  LOL

---

### Post by Bigneil on 2008-11-18
I would also like to retract my statement about xp being superior. i was basing my opinions on an OS that had taken years to modify and fiddle about to get it to work properly. i still have a few minor compatibility issues with heron but, when i look at the sparse dated looking xp 'fresh install' i think where's all my programs gone??  why is there some grass?? and where are all my icons??  i can't do any thing! where is my anti virus??......when i start heron, i know that i can draw from a vast choice of open source software :):):) and very qiuckly create a computer environment that i am happy with:):) some of the software is a little bit cookie but that is the magic of ubuntu:):)

unfortunatly i still have to use my mp3 player and print stuff so dual boot it is

Can any body give me a clue on default OS  :confused:

---

### Post by Het Irv on 2008-11-19
Its pretty easy to change the defualt, you just have to edit your menu.lst file for GRUB.

Go into the terminal and type```
gksu gedit /boot/grub/menu.lst
```
Once that opens look for the line that says "Default Num"  This controls which entry is the default one.  If you scroll to the bottom you can see what the entries are so you can count and see which one is XP.

---

