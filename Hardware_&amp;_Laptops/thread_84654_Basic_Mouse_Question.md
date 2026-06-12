---
title: "Basic Mouse Question"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by greenwom on 2005-10-31
Well, Ive gone through the forums a bit and read the wikis but I'm still having a problem.....

I have a basic 3 button mouse pluged into my box, I tried to plug in a P/S2 optical 5 button mouse (by GE).  Mouse doesn't work.

I've played with the xorg.conf settings a bit but every time I plug it in I get no mouse movement, I have gotton the right and left buttons to work but that's it.

I have restarted my machine after each change.

I've tried by changing the buttons option to 7 and the zaxis.. portion to  
"6 7" in xorg.conf.   Any recommendations?  I've searched the forums and googled it to death......

---

### Post by James Reed on 2005-10-31
Try changing mouse button in conf to "4 5". This got mine going properly

---

### Post by greenwom on 2005-11-02
From what I've read, it looks like it's a port problem.  The PS/2 support under linux can't handle the laser... So I've gathered from google.  I borrowed a USB adapter from my other machine (that needs to keep it)  an it works.  

I still want to know how to get this to work.  IS there some BIOS/ package function that emulates USB support for the PS/2 port?   :confused:

---

### Post by ionophore on 2005-11-03
I am no expert, but what is the value of the "port" parameter in your xorg.conf?  Several months back i was having some mouse problems on another distro and changing up:

Option    "Protocol"    "IMPS/2"
for 
Option    "Protocol"    "PS/2"

in xorg.conf solved my problem.  Although it's just a wild guess, that may be a place to start working from.

[edit]:  Here is a good place to start looking, in case you haven't found it already:
[http://www.x.org/X11R6.8.2/doc/mouse.html](http://www.x.org/X11R6.8.2/doc/mouse.html)

---

### Post by greenwom on 2005-11-03
well I tried your change PS/2 and ps/2 no joy.

Don't you hate how this stuff gets you, until you get it fixed~!!!!!!

I'll try the link

---

### Post by ionophore on 2005-11-03
When you say your mouse brand is "GE" ... what does that mean?  GE = General Electric to me....

I notice that the page i sent you has a number of entries about mice by Genius, if that's what you mean by GE...

[edit]:  Also, are you getting any mouse-related messages in /var/log/Xorg.log?

---

### Post by greenwom on 2005-11-04
GE does = General Electric.  I tried a number of configs (a few messed the system up at boot) :)  

I'll check into the log file and edit the post when I get back to the house.
thanks

---

### Post by greenwom on 2005-11-07
Well I gave up on the PS/2 mouse and got a USB. 

Not a real fix though (plus this deal has two wheels and 9 buttons to set up)

---

