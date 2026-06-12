---
title: "The Aiptek Tablet"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by MistaED on 2005-10-24
Hello, I use a Medion Aldi tablet USB on my computer which I've persevered with since Ubuntu Hoary 5.04. It is auto-detected as an aiptek generic device. It has been a hassle to even figure out what to even put in xorg.conf let alone realise the xorg driver is old and useless. I always need to replace the Xorg input driver from the one at aiptektablet.sourceforge.net so I can get proper absolute screen input and pressure sensitivity. I've finally got something to work when I put this into my xorg.conf:

```
Section "InputDevice"
  Identifier "pen"
  Driver "aiptek"
  Option "Device" "/dev/input/aiptektablet"
  Option "Type" "stylus"
  Option "Mode" "absolute"
  Option "Cursor" "stylus"
  Option "PressCurve" "0,5,95,100"
  Option "zMin" "0"
  Option "zMax" "512"
  Option "zThreshold" "0"
  Option "USB" "on"
  Option "KeepShape" "on"
EndSection
```

(I set hotplug to symlink whatever the /dev/input/eventX is as /dev/input/aiptek, maybe the Ubuntu development team can have this set up in scripts for future releases?)

I've managed now to get Photoshop 7 under wine to work with pressure sensitivity, but The Gimp still has problems and there is still some quirkyness. With The Gimp, I've set it up in preferences and have got it to work, but when I let go of the pen, it still draws and it has locked up the cursor from exiting. I need to close the program with alt+f and scroll to quit with the keyboard to get my mouse back.

The problem is (I think) the kernel 2.6.10 uses an old version (v1.3) of the driver source when the latest I believe is around v1.9. So I decided to wait for breezy to come with kernel 2.6.12 and have the updated module source. 

I use breezy now and I still have problems with the gimp, but I haven't checked what version the module is now because I don't know how. I've run out of ideas into why this tablet doesn't work, and everyone seems to have the expensive wacoms and have more support.

Could someone please help? I have the v1.9 source code for the module from aiptektablet.sourceforge.net but I don't really want to recompile my own kernel just for this. Is there just a way I can compile & integrate the later module source and just replace the old one without recreating an entire kernel?

Thank you.

---

### Post by luopio on 2005-11-30
Any progress on this? I never got my tablet working under gentoo (only partially -> no pressure sensitivity) and I'd be interested to get it working here on breezy.

---

### Post by MistaED on 2005-12-02
Yay someone replied, hey Luopio,

Well I researched it more, and now I'm trying to push a patch to the main linux kernel source tree so they can move from v1.5 to v1.9 for the aiptek source (nfi on how to do this), hopefully dapper drake will then have good aiptek-based support then if I figure this out. I also want to push xorg 7.0 to use the latest X11 driver but one of them just said they will just have what they already have and make the user install it manually (wtf?). I still want to push the ubuntu developers or whoever is in charge of the usb detection scripts to add a simple detect hardware one which detects the right /dev/input/* and then sym-links /dev/input/aiptek to it.

For now, I have no idea on how to compile & replace the current module without making an entire kernel.

-MistaED

---

### Post by luopio on 2005-12-02
[QUOTE=MistaED]For now, I have no idea on how to compile & replace the current module without making an entire kernel.[/QUOTE]

AFAIK, you can compile the new module if you just install the kernel-headers for the kernel-version that you're running. Then download the sources for the driver and compile away. Because the basic ubuntu-sources already have the aiptek-driver as a module, you just replace the module file with the one that you've compiled. 

You can find the module-file the kernel is using like this: 
```
$ modprobe -l | grep aiptek
```

Let me know if it works 8)

---

### Post by MistaED on 2005-12-15
Hello Luopio, sorry I haven't replied in over a week. Basically, the unified package driver from aiptek.sourceforge.net just dumps the module source into the kernel header directory and tells me to compile it myself. Now I have nfi on how to do this. I've compiled my own kernel in the past with slackware, but I don't really know how to compile a single module like this. If I know how, I would gladly try it and share my experience with you. 

At the moment I have dual-booted into windows to run my tablet (making a nice christmas card :) ) but I'd rather be using it in ubuntu. I've read our troubles are because of mandrake compatibility, so they disabled proximityOut or something. Maybe I can comment it back, or just leave it as the module source indicated that they're using some sort of a timer for this instead. The ```
$ modprobe -l | grep aiptek
``` gives me v1.5 as the one currently used.

-MistaED

---

### Post by luopio on 2005-12-16
Hi! I'm quite sure that you could compile the module with just the headers for the kernel, but I guess it'll be easier to compile it all together if that is what the module creators want :). 

Then I guess one has to go about like this for the kernel compilation: 

**Step 1: Get the kernel sources, unpack, link and use your old configuration**
```
sudo apt-get install linux-source-2.6.12
sudo tar xjvf /usr/src/linux-source-2.6.12.tar.bz2 /usr/src
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
sudo cp /boot/config-2.6.12-10-686 /usr/src/linux
```
**Step 2: Install the module sources**
I'm not sure how this is done, but you've obviously done it already...
**Step 3: Compilation**
Because the old configuration should work (aiptek is enabled, etc), we'll just compile the lot. 
```
sudo make
sudo make modules_install 
sudo make install
```
**Step 4: Make it boot**
Oh man. This is a lot easier with update-grub script :)
```
sudo update-grub
```
**Step 5: Boot the new kernel**
**Step 6: PROFIT!!! :cool: **
**Step 7: Tell me that it works beautifully**

I'll try to get the tablet working next year when I get it back from a friend.

[EDIT] Oh yeah, just remembered.. there is the "debian-way-of-installing-a-kernel-from-sources" which involves using "kernel-package" (in the repos) to make kernel-deb-packages and then installing those. I've used it, but can't remember how it went.. the forums are full of howtos anyway.. and call me old fashioned, but i just like the "manual" way of compiling ;)

---

### Post by luopio on 2006-01-24
Hello again. I noticed that bheadley took over the sf.net project again and started doing stuff. I got gaiptek from CVS and it compiles just fine. The tablet won't work fully tho'. 

You mentioned that you compiled the xserver-driver manually. How did you do it? I just took it from CVS and "imake" only produces:
```
Imakefile.c:34: error: Imake.tmpl: No such file or directory
imake: Exit code 1.
  Stop.
```

If I could get that compiled, then I could waste some time compiling the kernel driver and finally.... write a bloody howto so that other ppl could get theirs working as well :)

---

### Post by luopio on 2006-01-29
I installed the newest kernel and xserver drivers from CVS and finally the tablet did something different.. I seem to have pressure sensitivity, but the cursor warps around and the tablet is even less usable than before. 

Anyway, I made a **howto** and you can find it [here]("http://www.ubuntuforums.org/showthread.php?t=122735"). Try if the newest stuff solves your problems (some ppl report success on the mailing list)

---

