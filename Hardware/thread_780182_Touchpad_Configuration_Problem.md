---
title: "Touchpad Configuration Problem"
date: 2008-05-03
forum: Hardware
---

### Post by MasterNetra on 2008-05-03
Hi, I orginally was running Ubuntu 8.04 (64bit) and converted it to Kubuntu 8.04 (Not sure if it is still 64bit version) after i did i found that there is no links or seemly controls for the touchpad. I went into adept and installed the "Touchpad" app which was to suppose to let me configure the touchpad but i can't find anyway to access it! Yes i tried looking in System Settings > Keyboard & Mouse as well as all through the menus.

Whats going on? How can i access it?

---

### Post by roma2 on 2008-05-03
which synaptics touchpad driver are you using? Check if you have xserver-xorg-input-synaptics installed and that the driver is loading in your xorg.conf file: 

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

A synaptics touchpad on most laptops should have been detected and configured automatically for you. What kind of laptop are you using?

---

### Post by MasterNetra on 2008-05-03
Dell Latitude D530. The touchpad works, there just seems to be no way to configure it. Also that entry is there.

---

### Post by Zorael on 2008-05-03
See [http://qsynaptics.sourceforge.net](http://qsynaptics.sourceforge.net).

---

### Post by lswest on 2008-05-03
also, to run the program you seem to have "lost" try typing its name in the Konsole.

---

### Post by MasterNetra on 2008-05-03
> **Zorael said:**
> See [http://qsynaptics.sourceforge.net](http://qsynaptics.sourceforge.net).

Ok...So what should i download from there and how do i install it?

> **lswest said:**
> also, to run the program you seem to have "lost" try typing its name in the Konsole.

I don't know what its actual name is. I type Touchpad and it says something like bash not found or something.

---

### Post by Zorael on 2008-05-03
> **MasterNetra said:**
> Ok...So what should i download from there and how do i install it?
Well, no, I was mostly referring to how updates to X broke things and that he stopped developing it.

Lacking a front-end, you could try to do things manually. Make sure to enable the "SHMConfig" option in that inputdevice section in your xorg.conf.
```
	Option		"SHMConfig"	"on"
```
See the man-page for **synaptics** to see which options are available. Again, I don't think most/many will work.

To apply a new setting, use the **synclient** command; **synclient Option=value**. You can also add these as options in your xorg.conf if they're something you consistently want.

Finally, the "Touchpad" program you're mentioning is likely **gsynaptics, ksynaptics** or **qsynaptics**. I'm unsure as to how well they work nowadays.

---

### Post by MasterNetra on 2008-05-03
Sorry don't know what synclient is nor do i know how to get to it. x.x Program wise synaptic's package manager doesn't list such "synclient" when i search for it. All that comes up is xserver-xorg-input-synaptics which has been installed sense even before i converted from Ubuntu.

Also SHMConfig remains disabled it seems:

(In Konsole)
<removed>:/etc/X11$ sudo synclient Option=value
[sudo] password for <removed>
Can't access shared memory area. SHMConfig disabled?
<removed>:/etc/X11$ synclient Option=value
Can't access shared memory area. SHMConfig disabled?

(<removed> = removed info that was removed from post for the sake of secuirty)

I have the SHMConfig Option set to on then changed to true to see if it helped any. Nothing.

---

### Post by Zorael on 2008-05-03
And you did restart X after changing said xorg.conf file, right? I just tried it and it worked for me, at least.
```
zorael@sunspire:~$ synclient lala=whee
Unknown parameter lala
*<note: no mention of SHMConfig>*
```

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"on"
EndSection
```

As for available options, you can read the man-page over at [http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics). "Options=value" was merely an example. :>

---

### Post by MasterNetra on 2008-05-03
oops I thought all that was needed was logout... I'll try that first >.<

........

Well that enabled SHMConfig

........
I went to that man page you listed and the commands work. I was able to disable the tap click as well as the touch pad's scroll thing using synclient Touchpad=2 command. Thanks you for your help! Even if i don't have a graphical interface to adjust touchpad at least i have some way to do it. :)

---

### Post by roma2 on 2008-05-03
> **MasterNetra said:**
> Dell Latitude D530. The touchpad works, there just seems to be no way to configure it. Also that entry is there.

My bad, I misunderstood your post.

---

### Post by MasterNetra on 2008-05-03
ack.. I finally figure how to install TouchFreeze only to find it doesn't have any effect save for disabling the quick-fix solution "synclient TouchpadOff=2" >.>

---

