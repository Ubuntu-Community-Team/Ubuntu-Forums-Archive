---
title: "disable touchpad"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by pravit on 2005-05-28
Hi,
New to Linux. I want to disable the touchpad since I keep accidentally touching it and moving all over the place. I tried editing /etc/xorg.conf and adding the option "TouchpadOff" "1" under the Synaptics section, then rebooting, but that didn't do anything.

If possible I'd like to turn off the touchpad but keep the little pointing stick in the middle of the keyboard working.

Thanks for any help!

Pravit

---

### Post by tread on 2005-05-29
In the ServerLayout section of your xorg.conf, there should be two InputDevices, one would be the pointy thing and the other the synaptics touchpad. Try commenting out the Synaptics Touchpad there. And restart X of course :)

---

### Post by pravit on 2005-05-29
No luck, the touchpad still works. This is what I did to xorg.conf(I did reboot):

#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#       Option          "SendCoreEvents"        "true"
#        Option          "Device"                "/dev/psaux"
#        Option          "Protocol"              "auto-dev"
#        Option		"HorizScrollDelta"	"0"
#	Option		"TouchpadOff"		"1"
#EndSection

#	InputDevice	"Synaptics Touchpad"

---

### Post by Arthemys on 2005-05-29
If you're using an IBM ThinkPad you can go into your BIOS and disable the touchpad, this probably holds true for many other makes / models.

---

### Post by pravit on 2005-05-29
Yeah, I disabled it using the bios, but this disables both the pad and the pointy thing! :D It seems nitpicky but when I'm at home I use the mouse and when I bring the laptop with me somewhere I use the pointy thing. I pretty much never use touchpad. So I was hoping there was some simple solution I could do through the GUI...

---

### Post by n!k on 2005-05-31
I'm lookng for the same thing. I always bump the damn touchpad when typing and I hate it to death. I use a USB mouse for everything.

I tried this once on another laptop and lost all mouse support completely. Had to use a rescue disk to fix that one.

Anyone have any ideas? I'm about ready to toss this thing.

---

### Post by Locomorto on 2005-05-31
Try uncommeting the line. That normally helps ;).

---

### Post by dejitarob on 2005-06-05
Nope still works surprisingly.

---

### Post by HippoMan on 2006-02-26
Has anyone figured out how to get the synaptics touchpad to totally, completely, and irrevocably be turned off while running kubuntu under Breezy on my Dell Inspiron 9300?  I don't want tapping, I don't want sliding, and I don't want ANYTHING to work on the touchpad.  I want it to behave like a dead piece of metal with no more functionality than the rest of the material that makes up the case of my machine.

Everything I have tried has no effect, and I can't kill the touchpad functionality.  It keeps on responding to touches, slides, and taps, no matter what I do.  It's like I'm in the movie *Night Of The Living Dead Touchpad*.

Here are all the things that I have done and am doing:

1. I have the following items installed via apt:

    ksynaptics
    xorg-driver-synaptics

2. I have the following lines in xorg.conf:
```
  Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"      "true"
        Option          "Device"              "/dev/psaux"
        Option          "Protocol"            "auto-dev"
        Option          "HorizScrollDelta"    "0"
        Option          "SHMConfig"           "on"
  EndSection
``` 
3. I run the following command:

   synclient TouchpadOff=1

4. I went into **KDE Control Center->Peripherals->Touch Pad** and I set the following items:

... in the **General** section: **Touch Pad** is **off**, **Disable touchpad when typing** is not set, and **ALPS touch-pad** is not set.

... in the **Tapping** section: **Enable tapping** is not set, and **Enable faster-tapping** is not set.

... in the **Scrolling** section: **Enable horizontal scrolling** is not set, **Enable vertical scrolling** is not set, **Enable circular scrolling** is not set, **continue scrolling** is not set, and **cursor movement** is not set.

But still, even after rebooting, my touchpad is still active.  Earlier, I was running debian/testing on that same machine, and doing numbers 1, 2, and 4 did indeed successfully kill my touchpad.

What do I have to do under kubuntu/breezy to kill it in the same way?

Thanks in advance.

---

### Post by pestypest on 2006-03-21
[QUOTE=pravit]Hi,
New to Linux. I want to disable the touchpad since I keep accidentally touching it and moving all over the place. I tried editing /etc/xorg.conf and adding the option "TouchpadOff" "1" under the Synaptics section, then rebooting, but that didn't do anything.

If possible I'd like to turn off the touchpad but keep the little pointing stick in the middle of the keyboard working.

Thanks for any help!

Pravit[/QUOTE]
Ok check out this link, it should help you,  [http://www.ubuntuforums.org/showthread.php?t=143095](http://www.ubuntuforums.org/showthread.php?t=143095).  enjoy let  me know if it works for u ;)

---

### Post by Acunga on 2008-03-20
How to kill the touchpad softwarely on Ubuntu forever?I did the same thing like HippoMan but in vain

---

