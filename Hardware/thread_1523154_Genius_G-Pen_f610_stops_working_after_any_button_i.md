---
title: "Genius G-Pen f610 stops working after any button is pressed"
date: 2010-07-03
forum: Hardware
---

### Post by zidarsk8 on 2010-07-03
Okay, I'm sorry for posting another thread about G-pen. I have seen that there are many of them already, but I've went through most of them and nothing worked.

so here is my problem:

my genius g-pen f610 tablet works fine, and it moves the cursor around when the pen is just above the tablet, but as soon as I touch the table (or press any of the two buttons on the pen) my cursor stops moving if the pen doesn't touch the tablet... pressing on the different pars of the tablet with my pen still works and moves the cursor, just i can't move it without touching the tablet (having it lifted just above it)

if i pull the pen away from the tablet (more than the inch of hover space where it should still register) and then put it back, it starts all over, works fine until i touch anything. 

i am running Lucid Lynx 64bit 

and the problem was the same on clean install and on 32 bit version 
I've tried  installing xserver-xorg-input-wizardpen and fiddling around a bit but nothing i do seems to change the behavior.


If anyone could please help, I would greatly appreciate it. I know it doesn't seem like a big problem, but it's the same as not having a tablet at all, since i can't get any drawing done with it.

PS: i'm running 9.04 on my laptop where it works fine. but with 9.10 and 10.04 i've been having problems

---

### Post by Favux on 2010-07-03
Hi zidarsk8,

I believe that's a rebranded Waltop tablet.

The LWP (linuxwacom project) has set things up so Waltop tablets can run with it's drivers.  However the Waltop kernel drivers don't quite work yet.  Supposedly some patches are coming.  In the meantime you can use the WizardPen driver.  See:

[http://ubuntuforums.org/showpost.php?p=9393179&postcount=1002](http://ubuntuforums.org/showpost.php?p=9393179&postcount=1002)

[http://ubuntuforums.org/showthread.php?t=1475433](http://ubuntuforums.org/showthread.php?t=1475433)

Good luck!

---

### Post by zidarsk8 on 2010-07-04
Thank you for those links, but I've tried them and links from those thread, and link from those links ... 

but it would seem i just can't get and different kind of behavior from my tablet,

i tried editing those config files,... and just to see if they do anything i even deleted them, and it's all still the same.

It's really kinda frustrating .. :(

---

### Post by Favux on 2010-07-04
Then you want to check:
```
xinput --list
```
and Xorg.0.log in /var/log and see what if any driver has your G-pen.  Does the G-pen work correctly in Windows?

---

### Post by zidarsk8 on 2010-07-26
a little update for anyone else who might be having similar problems

the big issue was that i wasn't using any drives for my device! because 
```

Section "InputDevice"
        Identifier      "WALTOP Slim Tablet"
        Driver          "wizardpen"
        Option          "Name"          "WALTOP Slim Tablet"
        Option          "Device"        "/dev/input/event3"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"20000"
	Option		"BottomY"	"12500"
EndSection

```
I tried this, and it would seem that my tablet switches event number on every restart. So far I've had a random number from 2 to 5.
so if i want my tablet to use this driver and to work normally, i have to see witch event it triggers (i do that wit wizardpen-calibration /dev/input/evert<numbers from0 to 7>) and after that i have to edit the xorg.conf and i have to restart xserver.

That is quite annoying, and i have spent a lot of time trying to make it work, just to figure out that i wasn't doing anything.


So at least now i know how to get it working, but if anyone knows how to fix that event number problem i would be very happy. 
also if i unplug and plug it in again, the event stays the same but i still have to restart xserver , so it's all very weird to me.

Any suggestions are very much appreciated. Thank you.

---

### Post by Favux on 2010-07-26
Hi zidarsk8,

You want to see if you can figure out the pci usb by-path the Waltop is on.
```
dmesg | grep [Ww]altop
```
and
```
ls -l /dev/input/by-path
```
See Apppendix 1 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by zidarsk8 on 2010-07-27
all i got was
```

zidar@zidar-desktop:~$ dmesg | grep Waltop
zidar@zidar-desktop:~$ dmesg | grep waltop
zidar@zidar-desktop:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2010-07-27 15:07 pci-0000:00:1d.0-usb-0:2:1.0-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2010-07-27 15:07 pci-0000:00:1d.0-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2010-07-27 15:07 pci-0000:00:1d.2-usb-0:1:1.0-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2010-07-27 15:07 pci-0000:00:1d.2-usb-0:1:1.0-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2010-07-27 15:07 pci-0000:00:1d.3-usb-0:2:1.0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 9 2010-07-27 15:07 pci-0000:00:1d.3-usb-0:2:1.1-event-mouse -> ../event6
lrwxrwxrwx 1 root root 9 2010-07-27 15:07 pci-0000:00:1d.3-usb-0:2:1.1-mouse -> ../mouse3

```

so i don't see how this is any help to me. i still can't see withc "mouse event" is my tablet.

and to make things worse, i had to turn off the driver, cause it just happened when i started my comp today, that my mouse was on event3 that i had in xorg.conf for the tablet, and so my mouse wouldn't move from the top left corner of my screen .. it just flickered there.

---

### Post by Favux on 2010-07-27
It's not clear to me why waltop isn't bringing in the dmesg output.  But from what we have it looks like it should be:
```
"/dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-event-mouse"
```
If we get it right it should prevent the usb mouse from setting up on event3.

---

