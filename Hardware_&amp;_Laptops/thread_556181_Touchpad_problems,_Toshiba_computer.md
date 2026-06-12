---
title: "Touchpad problems, Toshiba computer"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by Kivrin on 2007-09-21
I have a Toshiba A25-S250 running Feisty Fawn. Up until three weeks ago the scroll function of my touchpad worked perfectly. Then I installed an update of something, the scroll function died, and the touchpad became wonky. 

Now, I've read about two dozen posts suggesting things, and have fought through two fun instances of blue screen of death because I've messed up edits of my xorg.conf. Nothing, so far, as worked. I'll run down what I've tried:

(1) gsynaptics. It insists that my SHMConfig is not set to true. It is set to "true." I've tried with "on", also, to no effect.

(2) qsynaptics. It refuses to work, claiming that I have not installed the Synaptics driver and have not turned on X shared memory config in XF86Config. I've installed the driver via Synaptics Package Manager, and I don't have an XF86Config file. 

(3) Editing the xorg.conf file. I've tried this a dozen times with a dozen different settings. I've told it to Load "synaptics" under the Section "Module". I've edited my Synaptics Section "InputDevice". Currently it reads like this, and is only extensive because it's the most recent thing I tried:

Section "InputDevice"
	Driver 		"synaptics"
	Identifier 	"Synaptics Touchpad"
	Option		 "Device"		 "/dev/psaux"
	Option		 "Protocol"		 "auto-dev"
	Option		 "LeftEdge"		 "1700"
	Option		 "RightEdge"		 "5300"
	Option		 "TopEdge"		 "1700"
	Option		 "BottomEdge"		 "4200"
	Option		 "FingerLow"		 "25"
	Option		 "FingerHigh"		 "30"
	Option		 "MaxTapTime"		 "180"
	Option		 "MaxTapMove"		 "220"
	Option		 "VertScrollDelta"	 "100"
	Option		 "MinSpeed"		 "0.09"
	Option		 "MaxSpeed"		 "0.18"
	Option		 "AccelFactor"		 "0.015"
	Option		 "SHMConfig"		 "true"
	Option		 "Emulate3Buttons"	 "on"
EndSection

I've added InputDevice "Synaptics Touchpad" under Section "ServerLayout". 

Nothing worked.

I'm at a loss here. I really want my scroll function back. Anyone else have suggestions?

(An interesting side note, my /proc/bus/imput/devices file is completely empty.)

---

### Post by hailtothethief on 2007-09-21
Ensure that **"SHMConfig" is set to "true"** in the "Touchpad" section of /etc/X11/xorg.conf

Using your method of choice, install the package **"gsynaptics"**

Restart your XServer: **Ctrl + Alt + Backspace**

Go to **System -> Preferences -> Touchpad**

**Configure** it as you would see fit.

---

### Post by Kivrin on 2007-09-21
> **hailtothethief said:**
> Ensure that **"SHMConfig" is set to "true"** in the "Touchpad" section of /etc/X11/xorg.conf

Using your method of choice, install the package **"gsynaptics"**

Restart your XServer: **Ctrl + Alt + Backspace**

Go to **System -> Preferences -> Touchpad**

**Configure** it as you would see fit.

Yes, I did all of those things, as I mentioned. Please see my post, because gsynaptics did not work.

---

### Post by KaYnemO on 2007-09-23
> **Kivrin said:**
> Yes, I did all of those things, as I mentioned. Please see my post, because gsynaptics did not work.
yep.... that same problem here on Acer Aspire 5670 with Feisty Fawn and I am also at loss... no cure????

---

### Post by strabes on 2007-09-23
Upgrade to gutsy. Many bugs are fixed.

---

### Post by KaYnemO on 2007-09-24
well I am running Feisty Fawn - that is the latest of ubuntus, right?

---

