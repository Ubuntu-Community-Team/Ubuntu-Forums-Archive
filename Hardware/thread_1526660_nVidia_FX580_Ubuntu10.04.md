---
title: "nVidia FX580 Ubuntu10.04"
date: 2010-07-08
forum: Hardware
---

### Post by ndhertubu on 2010-07-08
I have a new Dell Optiplex 380 with Quadro Nvidia FX580 graphics card (this
uses a DVI connector on the back of the PC and DVI connector on the monitor). 
Under Windows7, I can use it without problem. 
 
I downloaded Ubuntu10.04 on a CD, booted the system from the CD 
I got an initial screen (darkpurple backgrond with a keyboard icon and a
circle at the bottom, then a black screen with a a cursor blinking in the
upper right corner, 
then: everything stays black...
(normally I should now get a purple-backgrounded screen with the word
Ubuntu and 5 dots below ...)
(the CD continues to load), everyhting stays black ...
 
On another Dell Optiplex 380 with no special graphics card (standard onboard
VGA), I can boot from the CD and get to the Install screen.
 
What can be done about this to make Ubuntu work with this nVidia FX580
graphics card ??

---

### Post by dabl on 2010-07-08
To boot the Live CD, you probably need to choose "Safe Graphics" from the initial menu -- I forget whether it is F4 or F6.

To resolve the transition from Grub to Plymouth to whatever the X system wants to use (nouveau driver), you probably will need this:  [http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

And then if you want 3D graphics (Desktop Effects), you'll need to enable Hardware Drivers and select the Nvidia driver.

---

