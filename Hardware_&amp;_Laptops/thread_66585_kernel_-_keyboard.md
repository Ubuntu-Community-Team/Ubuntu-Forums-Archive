---
title: "kernel - keyboard"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by Niker on 2005-09-17
Hi all,
I'm trying to compile my custom kernel and finally got it booting tho now I'm stuck at a point where the keyboard dosn't work at all. All the modules and hotplug stuff loads then it gets to gdm but fails and complains that there is no /dev/../mice
but finds the kboard. 

The keyboard still dosn't work since I can't write anything if I run the rescue mode of the kernel so I'm wondering what options I need to compile into the kernel or as a module to get it to work. 

I'll paste the .config file tomorrow if this will help you guys more.

specs: fujitsu siemens amilo M1425 laptop...

---

### Post by Niker on 2005-09-18
xorg log:
```

--snip--
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(EE) xf86OpenSerial: Cannot open device /dev/input/mice
	No such file or directory.
(EE) Configured Mouse: cannot open input device
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
No core pointer

Fatal server error:
failed to initialize core devices

```

---

### Post by mlomker on 2005-09-18
It looks like your mouse isn't being recognized either.  Did you remove devfs?

---

### Post by Niker on 2005-09-18
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_SYSFS=y
CONFIG_DEVFS_FS=y


I guess you're refering to that one? Seems to be in place..

Tho it dosn't look like it's getting automounted, lemmi see if that's the problem

---

### Post by Niker on 2005-09-18
nope still the same issue. I can see the dev getting mounted and mice setting up when i boot the rescue mode but everything is still just plain dead. Only button that works is the 'suspend' button. Any other tips? Maybe I'm compiling something into the kernel that should really be a module to work?

---

### Post by mlomker on 2005-09-18
> Any other tips?

Is it a 2.6.13 kernel or ?  It has symbols that aren't present in 2.6.10.

---

### Post by Niker on 2005-09-18
nah it's the standard 
linux-source-2.6.12 
from the apt-get ubuntu linux-tree.

What are the patches for? I got the /usr/src/linux-patches/i386/2.6.12  but to me it seems like 90% of the are allready patched on the 2.6.12 kernel? And what's the proper way of patching it? I bunziped the patch.2.6.12-8.13.bz2 and then patched it normally with patch -p1..

Maybe there's another way of using the .sh script that came along that package?

---

### Post by mlomker on 2005-09-18
[QUOTE=Niker]Maybe there's another way of using the .sh script that came along that package?[/QUOTE]

Good question regarding the patches.  From what I could tell the patches are already applied but the linux-tree downloads them anyway in case you want to apply them to a clean linux source.  I believe it is unecessary to reapply to their provided source.

By the way, 2.6.12 is not available for Hoary, so you must be using breezy.  You posted your request in a Hoary board and that's why I was a bit confused.

FWIW I could never successfully recompile a Ubuntu-patched kernel that would even boot on my laptop.  I ended up going with clean 2.6.13 source and then applied the ck patchset.

---

### Post by Niker on 2005-09-19
ck patchset?

I finally got it working using the default .config that comes with the latest kernel and gets placed in the /boot dir. copied it over to my source, make oldconfig, compiled and it booted.. So I started to strip out from that config which atleast works from the start. Looks like there are alot of factors to get things working on a laptop. Atleast I could get rid of the main things that my laptop dosn't use.

btw is there any difference changing the pentium-pro 'which is default' to pentium4 m? Somehow I doubt this has any inpact on the performance overall.

---

### Post by mlomker on 2005-09-19
> ck patchset?


[Here](http://members.optusnet.com.au/ckolivas/kernel/) 

> 
btw is there any difference changing the pentium-pro 'which is default' to pentium4 m? Somehow I doubt this has any inpact on the performance overall.

I had assumed that you were already using the oldconfig.  Building a kernel using the oldconfig with no changes wouldn't work for me.

From a user perspective I didn't see any performance difference between my custom kernel and the stock on at all.  I suppose if I ran benchmarks of some kind that I might notice, but I haven't found a benchmark package for that.

That's why I'm running the stock kernel now--it's so much easier.  There's really no point in a custom kernel unless you need to build in a patch for an odd piece of hardware or something like that.  There's more bang-for-the buck by adding memory to your box or tweaking the startup scripts to speed your boot time.

---

### Post by Niker on 2005-09-19
thanks for all the info. I was mainly after to get bootsplash working but without luck, I juse ended up with a black screen and no boot so now I'm gonna go with the latest stable kernel and ck patchset, looks nice indeed.

do you have any idea if ubuntu pathes their kernel with it? If so then I guess there is no reason with compiling your own kernels if all the h/w works..

---

### Post by mlomker on 2005-09-19
> do you have any idea if ubuntu pathes their kernel with it? If so then I guess there is no reason with compiling your own kernels if all the h/w works..

Ubuntu has their own patchset, which you saw when you downloaded **linux-tree**.  That set is different than the ck set.  CK, however, is one of the most active people on the kernel mailing list and he's so smart that I don't understand a word that he says.   :smile:

---

### Post by Niker on 2005-09-20
it all works very well I might say. I even see a usplash on my boot which is very nice, hopefully there will be a ksplash to for kubuntu =)

---

### Post by colgate on 2005-10-09
Hi I have a quite similar problem with my Fujitsu-Siemens Amilo M1420 (like the niker one) and when I use suspend to disk everything is fine...but when i try to suspend to ram the notebook suspends nicely, then come back fine but with dead keyboard! The mouse works fine but no keyboard.....

do you have any idea about the cause? i can post some output of some command, if you ask....

thanks

bye

Fede

---

