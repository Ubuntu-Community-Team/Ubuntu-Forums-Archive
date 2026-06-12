---
title: "How to enable scrolling, etc. on touchpad?"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by swong1 on 2006-01-31
Hi, I have a Dell Inspiron 6000. I have been using Ubuntu since Hoary. The horizontal and vertical scrolling on the touchpad never worked. Double-tapping which worked previously on Hoary stopped working after upgrade. Synaptic package manager shows that I have xorg-driver-synaptic version 0.14.3. The relevant part of my xorg.conf looks as follow:

```

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "Emulate3Buttons" "true"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

```

How do I configure my touchpad to enable scrolling and double-tapping, dragging etc? Thanks.

---

### Post by kronepils on 2006-01-31
To enable scrolling, add 
 Option          "ZAxisMapping"          "4 5"
to your touchpad section.

I have the same options as you, and double-tapping, dragging etc (what that may be...) works for me!

---

### Post by swong1 on 2006-01-31
[QUOTE=kronepils]To enable scrolling, add 
 Option          "ZAxisMapping"          "4 5"
to your touchpad section.

I have the same options as you, and double-tapping, dragging etc (what that may be...) works for me![/QUOTE]

Thanks! I will try your suggestion and let you know the result.

---

### Post by swong1 on 2006-02-01
Nope, the trick didn't help. Scrolling and double-tapping still not working. Any ideas?

---

### Post by swong1 on 2006-02-03
bum.

Can someone please give me some pointers? Thanks.

---

### Post by scubajeff on 2006-02-04
Please refer to my old post:
[http://ubuntuforums.org/showthread.php?t=78904]("http://ubuntuforums.org/showthread.php?t=78904")

---

### Post by swong1 on 2006-02-05
[QUOTE=scubajeff]Please refer to my old post:
[http://ubuntuforums.org/showthread.php?t=78904]("http://ubuntuforums.org/showthread.php?t=78904")[/QUOTE]

Hi Scubajeff. Thanks for your reply. I found your post earlier, but I thought there is a difference between synaptic and alps touchpads so I didn't read further. Thanks for pointing me to the right direction.

I followed the instructions and it works like a charm! Thanks scubajeff!

Here's what I did:
```
cat /proc/bus/input/devices
....
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
....
```shows I have alps touchpad.
```
ls /usr/X11R6/lib/modules/input
```shows synaptics.drv.o is installed. Next I edited my xorg.conf file (new entries in **bold**)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    **"ALPS"**
EndSection

Section "InputDevice"
	Identifier  **"ALPS"**
	Driver      "synaptics"
**	Option	    "AlwaysCore" "true"**
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/input/**event2**" (depends on the output of cat /proc/bus/input/devices)
	Option	    "Protocol" "**event**"
[B]#	Option	    "ZAxisMapping" "4 5"
	Option      "LeftEdge" "120"
	Option      "RightEdge" "830"
	Option      "TopEdge" "120"
	Option      "BottomEdge" "550"[/B](set to 650 if you don't have horizontal scrolling)
[B]	Option      "FingerLow" "14"
	Option      "FingerHigh" "15"
	Option      "MaxTapTime" "180"
	Option      "MaxTapMove" "110"
	Option      "ClickTime" "0"
	Option      "EmulateMidButtonTime" "75"
	Option      "UpDownScrolling" "1"
	Option	    "LeftRightScrolling" "1"[/B](0 if no horizontal scrolling)
[B]	Option      "VertScrollDelta" "10"
	Option      "HorizScrollDelta" "20"
	Option      "MinSpeed" "0.45"
	Option      "MaxSpeed" "0.75"
	Option      "AccelFactor" "0.020"
	Option      "EdgeMotionMinSpeed" "200"
	Option      "EdgeMotionMaxSpeed" "200"
	Option      "CircularScrolling" "0"
	Option      "CircScrollDelta" "0.1"
	Option      "CircScrollTrigger" "2"
	Option      "SHMConfig" "true"
	Option	    "GuestMouseOff" "0"[/B]
EndSection

Reboot.

Now I have both horizontal and vertical scrolling plus tap+drag, etc. In firefox, horizontal scrolling is interpreted as forward and backward. To deactivate that, type about:config in the address window and set "mousewheel.horizscroll.withnokey.action" to "0".

---

### Post by vayde on 2006-02-07
I was able to get the scrolling working on my inspirion 9300.   Thanks to one and all for patiently re-posting the instructions.

Here's an interesting problem that has come up:

The scrolling only works when the requisite section in xorg.conf is set to the correct event, in this case '/dev/input/event2'  and the protocol is set to 'event'.  I get no results at all with the defaults of '/dev/psaux' and 'auto-dev'.

Here's the problem.  If I connect a usb mouse before I boot up, the events are set up differently, and 'event2' is no longer the touchpad.  If I attach the mouse after boot, there is no problem.

I could just remember to boot before connect mouse, but that strikes me as rather inelegant.  Can anyone tell me how to fix this little conundrum?

Thanks in advance

---

### Post by scubajeff on 2006-02-08
vayde,

you problem is related to dynamic naming of devices by udev. please read my post early on how to solve this.
[http://ubuntuforums.org/showthread.php?t=78904&page=5]("http://ubuntuforums.org/showthread.php?t=78904&page=5")

---

### Post by hw-tph on 2006-02-08
At least if you have an ALPS touchpad you might want to read [this thread](http://www.ubuntuforums.org/showthread.php?t=106369) as well.


Håkan

---

### Post by vayde on 2006-02-08
Thanks a ton guys.  I really appreciate the support.  Amazingly prompt, and helpful.

---

### Post by Commuto on 2006-03-07
Just another piece of information for all the ones struggling with such a basic (but fundamental!) issue:

I'm running Ubuntu 5.10.
On my Toshiba 5105-S501 laptop (Synaptics Touchpad), I was eventually able to get it working *very* easily thanks to [this](http://ubuntuforums.org/showpost.php?p=411672&postcount=9) input.
Basically I only had to replace the "buggy" (?)  /usr/X11R6/lib/modules/input/synaptics_drv.o driver with a more recent one.
No need to edit /etc/X11/xorg.conf in any way! :-D 

Now my cursor feels far more ..."precise" (kindof felling easier to click my target) and I got page scrolling working too! \\:D/

---

