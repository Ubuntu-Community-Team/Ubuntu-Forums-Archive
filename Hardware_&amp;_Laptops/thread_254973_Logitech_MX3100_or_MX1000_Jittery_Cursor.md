---
title: "Logitech MX3100 or MX1000 Jittery Cursor"
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by AndDroid on 2006-09-10
I'm having an issue with my Logitech MX3100 combo, specifically the mouse, which is an MX1000 laser mouse. The problem is that the mouse cursor is very jittery when moving, especially slowly, this happens under a 6.06 live cd session, a 6.06 install, and a 6.06 install in a VMWare session. It does not happen under Windows XP.

I thought that changing the xorg.conf file according to the MX1000 setup guides would help, but since my receiver is used for both the mouse and keyboard, the "Logitech USB Receiver" name that the guide used was not unique, and therefore did not work (Got an evdev error on starting X I believe).

If anyone has any information or ideas I can try to fix this, it would be greatly appreciated. I wanted to try to transition to Ubuntu from Windows, but this problem was so frustrating that I've gone back to Windows full time right now.

Thanks!

---

### Post by mitchtanz on 2006-09-11
Hi

Believe it or not, I had the reverse problem. My Logitech Mouse was jittery on XP and stable on Ubuntu. However my problem was a dodgy 5 year old USB port. They can be ok with one driver or device (such as the scanner works off it) but not another.

Sorry no exact solution but do check the USB port.

Best Wishes
Mitch

---

### Post by mitchtanz on 2006-09-11
Me again...just found this as I'm looking to get more out of my Logitech Mouse too..

HOWTO: Configuring Logitech mice in Ubuntu 6.06: New Guide  
[http://ubuntuforums.org/showthread.php?t=219894&highlight=Logitech](http://ubuntuforums.org/showthread.php?t=219894&highlight=Logitech)

Good Luck
Mitch

---

### Post by AndDroid on 2006-09-11
I tried that guide, and it had no impact on the problem.
I tried using a regular wired optical mouse, which worked perfectly, so I guess it couldd be a hardware issue, but it doesn't happen in other operating systems.

Anyone have any other idea?

---

### Post by mitchtanz on 2006-09-17
Is this is of any help

Enabling all of the functions on your Logitech MX1000 mouse
[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

I hope you solve the problem...

Best Wishes
Mitch

---

### Post by blindluck48 on 2006-10-14
Does that guide work for edgy?

---

### Post by purplerhino on 2006-12-07
I may be way off here, but if you just have a slight bit of jittery-ness, what are you using for a mouse surface?  If it's cloth, put it on your desk.

My MX1000 gets jittery on any cloth mouse pad, and it got too annoying to use.  Which is sad because I miss my death star mouse pad!

---

### Post by Rory_O on 2006-12-12
I'm having the exact same problem.  I also have a Wacom tablet that works fine, even in the same port.  The mouse itself is perfect in Windows.  I've set up evdev, and the buttons work, and upped the usb sampling rate (I think,  but I don't remember where I added it), and it's still jittery as all hell.  It's obnoxious and I really don't want to give up my mouse.

This is AMD64, 64 bit version.  I wouldn't be surprised if that had something to do with it, 64 bit seems to be problematic I've found.

---

### Post by Rory_O on 2006-12-18
Okay, I've finally got it figured out.  After observing the pointer movement in Windows, I noticed it was slightly jittery, but with 'Enhance Pointer Precision' turned on, it seems to interpolate it enough so that it wasn't an issue.

So if you have a jittery MX1000, I suggest trying these:

0) Clean the lens.  Grab a cotton swab, some alcohol and clean that thing.
0.5) Try a new surface.  Typical mousepads with repeating patterns aren't good for this thing
1) Change the USB polling rate to 1ms instead of 10ms
2) Get Lomoco from Synaptic and change the CPS to 2000 (sudo lomoco -g)
3) Open the Mouse preferences, under Motion and start playing with it.  Right now mine is set at 1/3 acceleration and full sensitivity.   

Adjusting the mouse preferences is critical.  Having the accel up too much seems to make it bounce around, but having it too low makes the cursor sluggish.  After all this, the mouse seems to feel more like an OSX pointer (bell curve accel) rather than a Windows pointer (liner accel).

Hope this helps someone else

---

