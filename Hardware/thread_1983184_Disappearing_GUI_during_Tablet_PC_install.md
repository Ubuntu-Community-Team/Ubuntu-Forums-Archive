---
title: "Disappearing GUI during Tablet PC install"
date: 2012-05-19
forum: Hardware
---

### Post by mishie on 2012-05-19
Hi there!

First time posting to the Ubuntu forms! Tried searching for the topic but not much seem to have come up.. apologies in advance if this has already been covered :)

Problem: Lost my GUI after following this page (wacom drivers)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

Laptop Model: Toshiba Tecra M7
[http://www.toshiba.ca/web/product.grp?section=1&group=223&product=6210](http://www.toshiba.ca/web/product.grp?section=1&group=223&product=6210)
(upgraded to 2g ram from 512)

I was operating off a fresh install of Ubuntu 12.04 32bit and had followed the instructions to try and get the 'tablet' part (pen recognition?) working.  Pretty much followed it exactly but can only get the command line after reboot.

Reinstalled the whole system and backed up /etc/X11/xorg.conf and followed the instructions again -- same thing happened (lost GUI).  Thought I might be able to get it back by restoring it but it didn't help (still no GUI).  Looked into the file and it seems to be empty?  Not sure what's going on right now but hope I won't have to re-install the OS for the third time lol!

Anyways, any help would be much appreciated... thanks! :)

---

### Post by Favux on 2012-05-19
Hi mishie,

Welcome to Ubuntu forums!

That shouldn't happen with a xf86-input-wacom compile.  I'm sort of interested in how you managed it.  :)

That model has been out over a year, correct?  I would think it should work out of the box.  If it is an ISDV4 model then it is probably the inputattach rule fouling you up.  Do you see a Wacom line in ***lsusb***?  What was the problem, the digitizer didn't respond to the stylus?

Ubuntu specific HOW TO's for compiling xf86-input-wacom:
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

Since X doesn't start it could be the 50-wacom.conf in /usr/share/X11/xorg.conf.d.  Does it look like the one on the BambooPT HOW TO link?

Did you use the **--libdir=/usr/lib** or **--libdir=/usr/lib64 flag**?

---

### Post by mishie on 2012-05-20
Thanks so much for the warm welcome & response Favux! :)

I turned on the laptop this morning and seemed to have lost the command line too.. ah well, re-install #3!

To answer your questions:
- yes, the model has been out for 1+ year (since '06 I think?)
- used --libdir=/usr/lib instead of the 64

I haven't done anything yet with this fresh install but going into *System Settings* there is already an option called *Wacom Graphics Tablet*.
Does that mean it is working out of the box already? Or do I have to enable it somehow?

Current ***lsusb*** shows the following:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

```

Output for /usr/share/X11/xorg.conf.d/50-wacom.conf
```

Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
        Identifier "Waltop class"
        MatchProduct "WALTOP"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
EndSection

```

Looks.. similar-ish to the sample on your link I think :)
Which direction should I take my next step?

---

### Post by Favux on 2012-05-20
With no usb digitizer seen lets try and determine if it is serial i.e. ISDV4 like I think.  Run:
```
sudo dmesg | grep ttyS
```
and let's see if we can figure out which serial port it is on.

---

### Post by mishie on 2012-05-20
Hmm... doesn't look like there is any output? Or at the very least, not showing anything.
I ran ***sudo dmesg*** by itself and all that's coming up are messages of my bluetooth re-enabling lol.  

Is there another place that we can check?

Thanks so much again for all your help! :)

---

### Post by Favux on 2012-05-20
Hmmm. Could these be usb?  Nope its ISDV4.  OK.

With the serial port we could find the PnP (plug-n-play) identifier with:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
It's probably ttyS0 or ttyS4.

But let's just assume inputattach is the problem.  So you should just need to comment it out. Change:
```

# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
```
to:
```

# Attach Wacom W8001 devices
#SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"
or
#SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5|WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"

```
You likely have a WAC* and not a FUJ*.  So only need that line commented out.  But you're there, might as well do both.  Or some have both in one line, but not Precise I don't think.
Using:
```
gksudo gedit /lib/udev/rules.d/40-inputattach.rules
```
After a reboot you should see the digitizer in ***xinput list*** and hopefully it will be working.

---

### Post by mishie on 2012-05-20
Yepyep.. *40-inputattach.rules* is definitely two lines on Precise :)  
Just commented both out and rebooted.

***xinput list*** output as follow:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=15	[slave  keyboard (3)]

```

Opened Xournal and started scribbling on the screen lol.  Still nothing.  
Am I testing it right?

---

### Post by Favux on 2012-05-20
Yes.  The pointer arrow should track the tip of the stylus and eraser and you should be able to use them as left mouse buttons and to draw.

Because stylus and eraser are appended to the parent device it looks like the tablet is on xf86-input-wacom.  But let's check.  What is the output of?
```
xsetwacom list
```
and
```
xinput list-props "Serial Wacom Tablet stylus"
```

---

### Post by mishie on 2012-05-21
Very interesting! Learning lots of new stuff for sure :)
For some reason I thought it might have just been my stylus that was the problem -- went and bought a new one but that didn't work either.. lol!

***xsetwacom list*** output:
```

Serial Wacom Tablet stylus      	id: 14	type: STYLUS    
Serial Wacom Tablet eraser      	id: 16	type: ERASER   

```

***xinput list-props "Serial Wacom Tablet stylus"*** output:
```


Device 'Serial Wacom Tablet stylus':
	Device Enabled (117):	1
	Coordinate Transformation Matrix (119):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (245):	0
	Device Accel Constant Deceleration (246):	1.000000
	Device Accel Adaptive Deceleration (247):	1.000000
	Device Accel Velocity Scaling (248):	10.000000
	Device Node (235):	"/dev/ttyS4"
	Wacom Tablet Area (314):	0, 0, 30348, 18968
	Wacom Rotation (315):	0
	Wacom Pressurecurve (316):	0, 0, 100, 100
	Wacom Serial IDs (317):	144, 0, 2, 0, 0
	Wacom Serial ID binding (318):	0
	Wacom Pressure Threshold (319):	27
	Wacom Sample and Suppress (320):	2, 4
	Wacom Enable Touch (321):	1
	Wacom Hover Click (322):	1
	Wacom Enable Touch Gesture (323):	0
	Wacom Touch Gesture Parameters (324):	0, 0, 250
	Wacom Tool Type (325):	"STYLUS" (307)
	Wacom Button Actions (326):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Device Product ID (234):	1386, 144
	Wacom Debug Levels (327):	0, 0

```

---

