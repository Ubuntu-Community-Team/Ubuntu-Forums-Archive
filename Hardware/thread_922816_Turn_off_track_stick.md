---
title: "Turn off track stick"
date: 2008-09-17
forum: Hardware
---

### Post by Cl0ud9 on 2008-09-17
The track stick on my Dell laptop has developed a mind of it's own making it very difficult to get any work done. I can't seem to find any way of turning it off. Any suggestions?

---

### Post by gr3yhatt3r on 2009-02-09
I'm having the same problem.  I am dual booted with Vista and have been able to disable the track stick on the vista partition but I have been trying forever to disable it in the Ubuntu partition. I'm new to linux so any help would be greatly appreciated.

---

### Post by sudden0utburst on 2010-07-12
uh. im brand new to ubuntu but im a quick learner n figured this out here ya go it helped me-
go to system
, preferences, assistive technologies nfind mousepad.. urwelcome peace!

---

### Post by jdh4321 on 2011-07-09
**Disabling the track stick in Ubuntu**


To list all available input devices:

Open terminal and use....

 &#9121; Virtual core pointer                        id=2  &#9116;   
&#8627; Virtual core XTEST pointer                  id=4  &#9116;   
&#8627; Wacom Graphire2 4x5 eraser                  id=9  &#9116;   
&#8627; Wacom Graphire2 4x5 cursor                  id=10  &#9116;   
&#8627; Wacom Graphire2 4x5                         id=11  &#9116;   
&#8627; AlpsPS/2 ALPS DualPoint TouchPad            id=14  &#9116; 
  &#8627; Macintosh mouse button emulation            id=15  &#9116;   
&#8627; DualPoint Stick                             id=13  

&#9123; Virtual core keyboard                       id=3 
     &#8627; Virtual core XTEST keyboard                 id=5      
&#8627; Video Bus                                   id=6      
&#8627; Power Button                                id=7      
&#8627; Sleep Button                                id=8      
&#8627; AT Translated Set 2 keyboard                id=12
 
In this example its "DaulPoint Stick" or "id=14

Then Use:

 xinput -set-prop "DualPoint Stick" "Device Enabled" 0

Its just a switch and when you reboot your Laptop you may have to Re-Input 
the command...

Just save it to a note so you can copy and paste in terminal...

The best way may be to detach the Stick all together..



Hope this helps...

---

### Post by gtippitt on 2013-02-19
I have a wireless keyboard with mouse touchpad that drives me crazy when I'm typing and bump it.  The touchpad is fine when surfing, but when I'm doing serious typing, I want to disable the keyboard's pointing device and use a cordless mouse instead.

The post above helped me find the link below that had lots more info on the xinput command.

[http://cederlys.wordpress.com/2010/07/13/disabling-the-track-stick-in-ubuntu/]("http://cederlys.wordpress.com/2010/07/13/disabling-the-track-stick-in-ubuntu/")


I created a launcher to disable the touchpad with
==> xinput -set-prop "pointer:2.4 GHz RF Receiver" 146 0

and other launcher to enable the touchpad with
==> xinput -set-prop "pointer:2.4 GHz RF Receiver" 146 1

Good luck,
Greg

---

