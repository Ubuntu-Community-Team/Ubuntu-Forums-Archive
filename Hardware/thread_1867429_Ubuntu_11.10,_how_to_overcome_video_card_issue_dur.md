---
title: "Ubuntu 11.10, how to overcome video card issue during boot"
date: 2011-10-22
forum: Hardware
---

### Post by spx2000 on 2011-10-22
Hi guys.

I have a Kupa X11 tablet computer and have been trying to install Ubuntu 11.10 on my system with little  success.
I am pretty sure pretty sure the main culprit is the video card but not sure how to proceed

For those who don't know about this tablet,
It has an Intel Atom Oaktrail process cpu - Z670 with 2GB Ram
The integrated video chip is GMA 600, very similar to the infamous GMA 500 chip "poulsbo" (considered as the worst supported linux video ever)

Okay, I say to myself. No problem, if GMA 500 works, than a similar driver should work right.  if not, I will boot in VESA mode and go from there


I got it installed using alternative install CD and using the vga boot option.  But when I try to boot, the screen would not shown anything.  The boot into recovery prompt would work except the usb keyboard doesn't work when in recovery mode.


My questions is:
1) How can I really tell where the boot issue is?  Is there a log file.
2)Is there a way to boot with some kind of default VESA mode when system is starting up?  Grub won't recognize the vga option and said I have to use the gfxpayload option now
3) The core system seems to running fine, but when I plugged in a usb keyboard, it shows a message saying "a new low speed usb device is plugged in" and the keyboard will no longer response?
4) is there a way to boot with GUI but very generic and minimal set of drivers?

The tricky part about this is that this is a tablet computer with no physical.  But it has been running great on Win7 so I like to see if I can put my favorite OS ubuntu on it as well.

Kupa X11 full specs is here:
[http://www.kupaworld.com/en/product/kupaX11](http://www.kupaworld.com/en/product/kupaX11)

---

### Post by mikewhatever on 2011-10-24
Hi, and welcome to the forums.
Not sure what you've heard about the GMA500, aka Poulsbo, but the truth is, it doesn't work. The Linux support has been abysmal over the past three years, so much so, that Intel had not been able to make gma500 work with Intel's very own Moblin and Mego mobile platforms. How ironic it that, Intel's mobile platform does not work with Intel's mobile chip.

...to answer some of your questions

1)The logs are in /var/log/. Look at dmesg and Xorg log.
2)For the lack of any other option, vesa should be the default drive to load out of the box. For the 'vga=' alternative in Grub2, check out the link below.
[http://ubuntuforums.org/showthread.php?t=1357855](http://ubuntuforums.org/showthread.php?t=1357855)

3)Try looking at the /var/log/syslog to figure out what happens.
4)You could try drivers other then vesa.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsboAlternatives](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsboAlternatives)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by spx2000 on 2011-10-30
Next you so much for replying. I really want a tablet running Ubuntu and I thought Kupa X11 is an excellent balance between performance, battery life and price.  

I have done my searching on both GMA 500 and GMA 600 and read about the lack of support from Intel/ Imagination Technologies.
The part I don't really get is:
Since GMA 500, the "Poulsbo",  and its PowerVR SGX core is in several systems, including Android phones Droids, Iphone and ipad which all have lineage back to Linux, why can't their drivers to be used.

I also found following sources for GMA 600 and Oaktrail cpu but not sure where to go next:

[http://build.meego.com/package/files?package=kernel-adaptation-oaktrail&project=devel%3Akernel&rev=afe74ad3d89d62ee2b5fae88b15cb9f8](http://build.meego.com/package/files?package=kernel-adaptation-oaktrail&project=devel%3Akernel&rev=afe74ad3d89d62ee2b5fae88b15cb9f8)

The Kernel version is 2.6.37 and is back support in 11.04.  I am not sure what to do next from this point on.  I know Fujitsu Q550 uses the exact same CPU and GPU platform.  Anyone running that tablet can chime in would be great as well.  Thanks again for your help.

---

### Post by spx2000 on 2011-12-11
There is an effort to create proper Poulsbo (GMA 500) driver for linux:
[http://forum.pocketables.net/showthread.php?t=9107](http://forum.pocketables.net/showthread.php?t=9107)

Does anyone knows if Ubuntu will adopt this and would this driver work for GMA 600

---

