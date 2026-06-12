---
title: "Limited functionality with Wacom Bamboo pen &amp; touch tablet"
date: 2011-08-28
forum: Hardware
---

### Post by DuckDodgers on 2011-08-28
I recently switched from my old Wacom pen tablet to the pen & touch tablet (Model CTH-460).  To get it to work, I tried using this tutorial [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
only to come to several puzzling and/or frustrating dead ends.  
I then tried this one 
[http://ubuntuforums.org/showthread.php?t=1699650&highlight=wacom+touch+pen](http://ubuntuforums.org/showthread.php?t=1699650&highlight=wacom+touch+pen)

That worked a little better, but I still can't use the touch function on my tablet.  Worse, when I rest my hand on the tablet the 'hover' mode stops working until I move the pen away from the tablet.  Other than than that it works just like my old tablet, but with fewer buttons.

Any suggestions on how to get the touch function to work?

---

### Post by Favux on 2011-08-28
Hi DuckDodgers,

You went from a current HOW TO to an old "obsolete" PPA.  Since it installed a linuxwacom wacom.ko with dkms you have to remove the dkms implementation to get a newer wacom.ko.

CTH-460 isn't specific enough.  You'll need to post the Wacom line in the output in a terminal of:
```
lsusb
```
in order to determine the model.

---

### Post by DuckDodgers on 2011-08-29
Here is the output of lsusb

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 056a:00d6 Wacom Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


If you think it would be best to follow the first place I tried after backtracking with it I think the problem started on the third line 

> sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool


I thought that worked fine, but when I tried it again I noticed this after I pressed the y

> After this operation, 43.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

That's right I pressed y to say I wanted to continued and it acted exactly as if I pressed n.  I even tried to use a capitol Y, and pressing the n just to see what would happen and it was the same.  I'm pretty sure I've successfully used a sudo apt-get install command on this computer since I upgraded to lucid, so I really don't know what is going on there.

---

### Post by Favux on 2011-08-29
That happens occasionally to me too.  It seems to want to be case sensitive sometimes but then using Y works.  You just need to try again until apt-get downloads it.  Maybe the server was busy?

Alright the d6 (CTH460/K; Product ID = 0xd6) is one of the 5 "new" Bamboo Pen and Touches.  We discovered a few months ago that the new ones were using a new usb protocol.  Apparently because of a change in manufacturing.  The two Special Editions have four finger touch (4FGT).  And while yours and the two other non-specials have 2FGT like the 5 "old" ones they still have the new protocol.  Long story short something changed in the newer wacom.ko's (kernel drivers) and or xf86-input-wacom (X driver) so that the different protocol became obvious.  What happened is we noticed touch didn't work right.

So you can get the stylus, eraser, and tablet buttons working.  But touch will be flaky.  After getting some raw input data and doing a preliminary analysis things sort of stalled.  I think, from something said last week, they're going to get Chris one of the new Bamboo's so he can finally fix this.  He's the gestures guru.

You'll have to uninstall the dkms stuff.  That will be in /lib/modules/`uname -r`/updates/dkms.  Where `uname -r` is the current kernel you are on (enter it into a terminal and the output will be the kernel #).  I need to see the files in there to give the removal commands.  Wacom should be in the name most likely.

---

### Post by DuckDodgers on 2011-08-29
Well that's a short list.

> wacom.ko

---

### Post by Favux on 2011-08-29
Ok, without a version number it should just be:
```
sudo dkms remove -m wacom --all
```
to remove it.

---

### Post by DuckDodgers on 2011-08-29
It looks like it still needs a version number.  This is what I got as an output.

> Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>


Is there anything it will except as a version number?

---

### Post by Favux on 2011-08-29
I took a look at the deb from Ripps PPA and the dkms.conf says:
```
PACKAGE_VERSION="0.8.8"
PACKAGE_NAME="wacom"
CLEAN="cd src/2.6.30 && make clean"
BUILT_MODULE_NAME[0]="wacom"
BUILT_MODULE_LOCATION[0]="src/2.6.30"
DEST_MODULE_LOCATION[0]="/kernel/../extra/"
MAKE[0]="cd src/2.6.30 && make KERNEL_VER=$kernelver"
AUTOINSTALL="yes"
```
So I'm hoping this works:
```
sudo dkms remove -m wacom -v 0.8.8 --all
```

---

### Post by DuckDodgers on 2011-08-30
Still no good here is what I get.

> Error! There are no instances of module: wacom
0.8.8 located in the DKMS tree.

Since it's just one file is there any reason I couldn't just delete it in the file browser?

---

### Post by Favux on 2011-08-30
Since it is the only thing in .../dkms.  Why don't you just move or rename it and see what happens first?  Might want to do a:
```
modprobe --show-depends wacom
```
first.

---

### Post by DuckDodgers on 2011-08-30
Here is the output

> insmod /lib/modules/2.6.32-33-generic/updates/dkms/wacom.ko 


It seems more difficult to just move or delete than I thought

---

### Post by DuckDodgers on 2011-08-31
Is there any reason I can't just install the more up to date drivers?

---

### Post by Favux on 2011-08-31
The dkms module will overwrite any new module you install.

I don't understand why the command with the version # didn't uninstall it.  It should have:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  We've got the package name and version.  Double check the command when you enter it.

I guess try:
```
sudo dkms remove -m wacom
```

Does the PPA package show up in Synaptic Package Manager or Software Sources?  If so try uninstalling it also.

---

### Post by DuckDodgers on 2011-09-02
wow I don't know why I didn't think of synaptic package manager earlier.  When it works it works well.  At any rate I got rid of that pesky dkms stuff, and tried to get it to work with your tutorial.  I managed to get to the exact same place with a new wacom.co file, and similar problems.  I'm still working on step II of the tutorial because I'm having the weird Y means n on the sudo apt-get line in that section now.  I'll try again tomorrow and see how it works then.

---

### Post by DuckDodgers on 2011-09-08
Well after a week of trying to install everything from this site.
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
I've managed to get to the exact same problem. 
Is there any easy way to just disable the touch function?  It does kind of negate the advantage of this new tablet, buy I don't really need it.  My old wacom tablet was just dropped to many times.

---

### Post by DuckDodgers on 2011-09-08
wow apparently all I needed to do was to install the backport modules.  All I had to do was to type linux-backports-modules-input-lucid-generic for a search in ubuntu software center.  The gestures still don't work and the touch function is still hard to manage, but who cares the styles works with full pressure sensitivity and I can rest my hand on the tablet now.

---

### Post by Favux on 2011-09-08
Hi Duck Dodgers,

Good to know about the backport availability.  Wonder what's in it?

Well, as I mentioned on post #4 there is a problem with touch on yours and similar models because they are using a "new" USB protocol.  You can use the touch toggle script (part VII.) to turn touch off or use:
```
xsetwacom set "device name" Touch "off"
```
or in an appropriate xorg.conf.d snippet:
```
Option "Touch" "off"
```

The good news is Chris Bagwell just figured out the USB protocol and has a kernel patch for it.  I posted the link at the top of the BambooPT HOW TO a few days ago.  He just submitted a second version of that patch to the kernel (linux-input):  [https://patchwork.kernel.org/project/linux-input/list/](https://patchwork.kernel.org/project/linux-input/list/)  The site is currently down otherwise I'd link you directly to the patch.

So a fix for touch is now available.

---

### Post by DuckDodgers on 2011-09-09
That's great news I'll give it a try soon

And thank you for all of your help, you get a star:KS

---

