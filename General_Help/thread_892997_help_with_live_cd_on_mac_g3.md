---
title: "help with live cd on mac g3"
date: 2008-08-17
forum: General Help
---

### Post by huskyboi on 2008-08-17
it either sits at a black screen,also i got to command line but i dont remember the code to redo it. well i mean to auto set up x or whatnot, i just want to get this working and see if it runs okay


live-nosplash-powerpc video=ofonly gets me into text, now how do i set x up with the live cd? 

got it working 
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
modify &#8220;HorizSync&#8221; to 60-60 and &#8220;VertRefresh&#8221; to 75-117. Both are in the monitors section.
(#) at the beginning of the line containing &#8220;load dri&#8221;).
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line

    sudo killall gdm

    then

    sudo gdm start

first you may want to add a login
sudo adduser yourusername

answer the questions and your password when happy y to accept.

sudo killall gdm

then

sudo gdm start

then log it, worked for me
then disable dri

---

