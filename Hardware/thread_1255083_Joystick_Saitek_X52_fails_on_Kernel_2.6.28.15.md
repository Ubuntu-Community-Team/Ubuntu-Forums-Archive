---
title: "Joystick Saitek X52 fails on Kernel 2.6.28.15"
date: 2009-09-01
forum: Hardware
---

### Post by jomo-ub on 2009-09-01
I am using the X52-joystick since a long time - also with Ubuntu 9.04 since it's release. About 2 weeks ago I noticed that the X52 does not get discovered any more correctly (I use it in FlightGear) - while there is no problem with another USB-Joystick (see in the following the "Mega-World"). In the meantime i reinstalled Ubuntu and noticed:
1) with basic install (Kernel 2.6.28-11-generic I see in directory /dev/input/by-id

usb-04d9_0499-event-mouse
usb-04d9_0499-mouse
usb-Mega_World_USB_Game_Controllers-event-joystick
usb-Mega_World_USB_Game_Controllers-joystick
usb-Saitek_Saitek_X52_Flight_Control_System-event-joystick
usb-Saitek_Saitek_X52_Flight_Control_System-joystick

--> and that works fine  

2) then comes the upgrade to Kernel 2.6.28-15 and it does not function any more, and listing the /dev/input/by-id shows the same -- except** the last line is missing**!

The Desktop is a (2*) AMD Athlon(tm) 64 X2 Dual Core Processor 6000.
But same thing happens on my small
   Notebook with (2*) AMD Turino(tm) 64 X2 Mobile Technology TL-50
(by the way: It also works fine under Windows-XP)

--> So it looks to me like an USB-Sftw. problem - although I have no idea what in the (updated!) code could result in such a problem - i would have expected the USB-interface is yery much standadized!

Does anybody has an idea what it could be? 
And how to fix it?
I just like the flightgear!!!:(
thanks joe

---

### Post by Chris on 2009-09-02
I can't get my X52 to work on 2.6.28-15 either.  Running 64-bit Jaunty here.

I don't know if it worked before though, I haven't tried it in Ubuntu for a long time.

If it's suppose to be there then I'm also missing the last line.

Edit:
Check this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300143)
[http://catharnach.wordpress.com/2009/08/25/linux-and-the-saitek-x52/](http://catharnach.wordpress.com/2009/08/25/linux-and-the-saitek-x52/)

Apparently something has been blacklisted.  Anyone know a way to override this? Man, now I'm getting pissed.  First they killed my loop-aes now this.  "WONTFIX" Thanks a lot guys!?!

---

### Post by jomo-ub on 2009-09-02
Thanks a million -- i was not that positively surprised since years: That help was very fast and correct 
    **it works fine with 2.6.28-14**
thanks
joe

---

### Post by Capt. Blackwood on 2009-09-03
I'm using Jaunty 9.04, any way to find out what my kernel is and how to set it up for my stick.
 
I've got an Saitek X52 i'd like to run with FS2004 :)

---

### Post by jomo-ub on 2009-09-03
have a look in UBUNTU MenuBar --> System -- Administration --> System-Monitor --> System

---

### Post by Chris on 2009-09-04
> **jomo-ub said:**
> Thanks a million -- i was not that positively surprised since years: That help was very fast and correct 
    **it works fine with 2.6.28-14**

Well, technically it's not a solution because by running an older kernel you are vulnerable to critical security flaws.

---

### Post by Capt. Blackwood on 2009-09-04
i'm running the lates kernel too, is this good or bad.

---

