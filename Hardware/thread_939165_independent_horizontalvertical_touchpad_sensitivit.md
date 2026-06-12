---
title: "independent horizontal/vertical touchpad sensitivity settings?"
date: 2008-10-05
forum: Hardware
---

### Post by n8han on 2008-10-05
I've gotten my HP 2133's touchpad almost exactly the way I want it with custom synaptic options, but one thing is still driving me crazy: the touchpad is much more sensitive vertically than horizontally. This is especially disorienting when going between this touchpad and one that has a standard 1:1 ratio.

The touchpad is much wider than it is tall, which is a good thing to have when the screen is also wide. But they screwed up (at the hardware level, as far as I can tell) in mapping this physical rectangle into a virtual square (why!!!!?). This eliminates the benefit of it resembling the widescreen, and in fact it's worse than if it were a square because horizontal acceleration is greatly reduced. I can track from the top of the screen to the bottom, but not from the left to the right (in one stroke). I can't speed it up any more without vertical being far too sensitive. And at any rate it's disorienting to use with such different scales for horizontal and vertical.

I would like to correct this in software, but surprisingly there doesn't seem to be separate horizontal and vertical speed factors among synaptic's myriad options. Maybe, though, there is some way to correct it in a higher level mouse driver, in X or the window manager or somewhere? Any clues? At this point I can't even find the right place to file an upstream synaptic feature request.

Nathan

---

### Post by tsaarni on 2008-10-06
I have the same problem with HP Compaq 2510p.  I asked about the problem in xorg mailing list and got [reply]("http://lists.freedesktop.org/archives/xorg/2008-September/thread.html#38981") which unfortunately is that there really doesn't seem to be any existing solution.  

Without knowing the details, I think it shouldn't be too hard to fix the driver but since previously I was not able to find any other reports about this issue I was wondering if my touchpad is defective.  It even says in the [Synaptics Touchpad Interfacing Guide]("http://www.synaptics.com/decaf/utilities/ACF126.pdf") in section 2.3.2 that *"All Synaptics TouchPad products are designed to scale their coordinates and pressure to the same standard range regardless of the actual size of the sensor"*.  So I'm  "happy" to find you are having the same problem ;-)  I can try to come up with a patch.

---

### Post by n8han on 2008-10-06
My guess is that someone at HP/Compaq decided to wander off the spec without thinking this one through. I wonder if it has the same behavior on Windows, or if they realized the mistake and added an "anisotropic" driver?

I'll have a look at the synaptics source and see if it's something I can hack into without giving up my life for two weeks. It doesn't sound like the driver maintainers are likely to do it, seeing as they're already on the right side of the spec.

Nathan

---

### Post by tsaarni on 2008-10-06
It could also be that Synaptics didn't make touchpads with different aspect ratios back 10 years ago when the Interfacing Guide was written.  The comment "same standard range regardless of the actual size" doesn't necessarily include aspect ratio variations that we're seeing, it isn't very clear...  

I wonder if there are any newer additions/extensions to the protocol described in the doc...  Touchpads might report the aspect ratio or physical dimensions just like they are reporting maximum ranges for the coordinates.  That would allow driver to adapt automatically.

---

### Post by tsaarni on 2008-10-06
Well, obviously this isn't *anywhere* near usable but at least it's something to play with:

```

--- xfree86-driver-synaptics-0.14.7~git20070706.orig/synaptics.c
+++ xfree86-driver-synaptics-0.14.7~git20070706/synaptics.c
@@ -867,6 +867,7 @@
 
     while (SynapticsGetHwState(local, priv, &hw)) {
        hw.millis = GetTimeInMillis();
+       hw.y *= 0.60;
        priv->hwState = hw;
        delay = HandleState(local, &hw);
        newDelay = TRUE;

```

To compile do the usual thing:

```

apt-get source xfree86-driver-synaptics
sudo apt-get build-dep xfree86-driver-synaptics

# modify the source like above but 
# with your own multiplier for y coordinate

make
sudo cp synaptics_drv.so /usr/lib/xorg/modules/input/

# restart xorg

```

---

### Post by n8han on 2008-10-07
Ha, we patched right past each other! I should have checked this thread again today (but it was kind of a fun codebase to dig into). I did the same as you, and then made it a configuration parameter. I think all that remains is to add it to the man page. My branch is here:

git clone git://technically.us/git/synaptics

This is SO much better than the crazy default tracking.

Nathan

---

### Post by n8han on 2008-10-07
I should add that I'm on Ibex; I don't know if Hardy is compatible with the synaptics HEAD I worked off of.

---

### Post by maxberger on 2008-11-03
Thank you guys for summing this up nicely (I have the same problem). Please consider adding your patch to:

[https://bugs.freedesktop.org/show_bug.cgi?id=18351]("https://bugs.freedesktop.org/show_bug.cgi?id=18351")

Thanks

---

### Post by slacy on 2008-12-09
I tried the simple "hw.y *= 0.60" patch, but it led to extremely erratic vertical motion after the patch, so I had to revert back to the old binary. 

It seems as though there is a more official patch underway.  You can follow its progress on:

[http://lists.freedesktop.org/archives/xorg/2008-November/040092.html](http://lists.freedesktop.org/archives/xorg/2008-November/040092.html)

(and follow-ups, which are numerous). 

I'm surprised that this hasn't been fixed yet, since a number of the recent 'netbook' computers use these style non-square-pixel trackpads.  My Lenovo S10 is just one such example.

---

### Post by ionman on 2009-11-16
Nearly a year later, I am still having this same issue with Ubuntu 9.10. A lot has changed since then, so what is the best way to go about solving this problem now? Is there anyway to change the values through xinput, or do I still need to be running some custom driver?

Thanks!

- ionman

---

### Post by tsaarni on 2009-11-16
The x/y sensitivity should be detected and adjusted automatically if you upgrade to xf86-input-synaptics 1.2.0.

---

### Post by ionman on 2009-11-16
> **tsaarni said:**
> The x/y sensitivity should be detected and adjusted automatically if you upgrade to xf86-input-synaptics 1.2.0.

Thanks! What is the best way to upgrade? I found the source and I have downloaded it. Should I just build and install that, or is there a package available somewhere?

- ionman

---

### Post by tsaarni on 2009-11-16
Somebody might have packaged it already but I didn't find any...  You should be able to build it from sources. For installing you can just copy it to /usr/lib/xorg/modules/input/synaptics_drv.so and restart xorg. Before compiling get build dependencies by running apt-get build-dep xserver-xorg-input-synaptics.

---

### Post by ionman on 2009-11-16
Thanks for your help! I downloaded the tar.gz from this site: [http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/](http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/)
and was finally able to build it. I also had to update my xorg-macros and that was a bit of a paint.

After I finally built it, I never ended up with a .so file. Did I build the wrong thing? I did:

./autogen.sh
make
sudo make install

Rebooted, and the sensitivity is still wrong, so I suspect it is still using the old driver. Do you know what I am missing here?

Thanks!

- ionman

---

### Post by tsaarni on 2009-11-16
Check the current driver version in /var/log/Xorg.0.log, it should say

(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.2.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0

If the synaptics module version is 1.1.2 you are still using the default driver.

I tested compiling the new driver too.  The .so file is under ./src/.libs/synaptics_drv.so. Regarding xorg-macros it would have been enough to just replace XORG_MACROS_VERSION(1.3) with XORG_MACROS_VERSION(1.1) in configure.ac as the default one seemed to work too.

---

### Post by ionman on 2009-11-16
Hooray! It works!

For those of you that are still struggling with this issue, here is the complete how to:

First make sure you have the build dependencies. In a terminal execute this command:

```
sudo apt-get build-dep xserver-xorg-input-synaptics
```

Download the latest version of the xorg-macros from here:
[http://cgit.freedesktop.org/xorg/util/macros/](http://cgit.freedesktop.org/xorg/util/macros/)

Extract the folder, and cd to that directory.

Install the newest macros:
```
$ ./autogen.sh
$ make
$ sudo mv /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.old
$ sudo cp xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4
```

Download the latest version of the driver from here:
[http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/](http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/)

Extract the folder, and cd to that directory.

Build and install the new driver:
```
$ ./autogen.sh
$ make
$ sudo mv /usr/lib/xorg/modules/input/synaptics_drv.so /usr/lib/xorg/modules/input/synaptics_drv.so.old
$ sudo cp src/.libs/synaptics_drv.so /usr/lib/xorg/modules/input/synaptics_drv.so
```

Reboot. Enjoy!

- ionman

---

### Post by hurgh on 2009-11-16
Thanks to all, 
I have just completed ionman's steps on my Lenovo S10 and it works great.

-Hurgh-

---

### Post by macjedimatt on 2009-12-15
I just followed your instructions using Jollicloud on my Lenovo S10 and the speed it great now but I seem to have lost the ability to tap. When I enable it in the mouse control panel it doesn't do anything. Any ideas? Thanks again!

---

### Post by macjedimatt on 2009-12-15
Ok just fixed my own problem. lol
 I made the following script:

```
#!/bin/bash

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Time" 32 180
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap durations" 32 180, 180, 100
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 8 0, 3, 0, 0, 1, 2, 3

```

and made it a startup application in the preferences.

---

