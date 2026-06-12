---
title: "Patched b43 for BCM94311MCG wlan mini-PCI (rev 02)"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by gdselzer on 2008-01-28
Has anyone had success (or even tried) with patching the b43 module for rev 02 of this card?  I've upgraded my kernel to the Hardy 2.6.24 using the script [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=646755").

[[COLOR="Blue"]Linuxwireless.org[/COLOR]]("http://linuxwireless.org/en/users/Drivers/b43#supported") says that b43 supports the rev 02 but that it needs patches.  The only place I've found any patches is in this [[COLOR="Blue"]maillist[/COLOR]]("https://lists.berlios.de/pipermail/bcm43xx-dev/2007-November/006240.html") from November.  I've emailed Larry from that posting to see if there are any newer releases but have not heard back yet.  I also don't really know how to apply that patch, so even if it is the newest (and correct one) I still don't know what to do with it.

The issue I have with it unpatched is that the module loads but nothing happens.  Nothing in dmesg, syslog or ifconfig.  Does anyone have this card that can confirm the same symptoms?

Just in case you're not sure if you have this card, lspci should return:

```
$ lspci |grep BCM
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
```

Anyone?

---

### Post by eggfoo on 2008-01-29
I am experiencing the same issue. Following a number of guides, including this one [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a14b8a20c3973fe959032bd1566ad35dceb30132](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a14b8a20c3973fe959032bd1566ad35dceb30132)
has not brought me much luck. The machine is an HP G6000, with the same chipset as you. I am running Gutsy 7.10.

---

### Post by gdselzer on 2008-01-29
That guide you mention worked perfectly for me in Gutsy.  I used step 2a and other than the occasional hiccup I have used ndiswrapper for several months with no problems.  It's the b43 driver in Hardy that is causing me problems now.

---

### Post by koobert637 on 2008-01-29
I have the same wireless card and successfully used this patch to patch the new 2.6.24 linux source to enable native wireless. [http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2](http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2)

best of luck!

---

### Post by gdselzer on 2008-01-29
I found that as well.  I've patched, recompiled the kernel and now I get b43 to load.  However, I don't see any wireless networks and I get this in my dmesg:

Registered led device: b43-phy0:tx
[   38.931917] Registered led device: b43-phy0:rx
[   38.932128] Registered led device: b43-phy0:radio
[   38.932356] b43-phy0 ERROR: PHY transmission error

Any idea what's causing the error?

Thanks

---

### Post by koobert637 on 2008-01-30
I received that same error in my dmesg, however I was able to connect to my wireless network without error. does "sudo iwlist wlan0 scan" show any networks?

---

### Post by gdselzer on 2008-01-30
sudo iwlist wlan0 scan returns

wlan0     No scan results

There are at least 6 networks that it could be picking up.  Interestingly, nm-applet is now starting to show one network.  If it were mine I might be in luck, but it is my neighbors (unfortunately).

Out of curiousity, which firmware are you using?

---

### Post by ItsManaged on 2008-01-30
> **koobert637 said:**
> I have the same wireless card and successfully used this patch to patch the new 2.6.24 linux source to enable native wireless. [http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2](http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2)

best of luck!
Thanks for the tip - yes I too am having this problem, and having little luck. I am wondering about the firmware (suggested when I enabled the restricted driver) (Gutsy) but have no idea how to find and remove the firmware that was installed, let alone install new firmware to test my guess. I didn't note what the firmware was or where it came from - some weird URL when I enabled the driver. (Just getting cocky  - doh!) Any help here appreciated.

...how do you apply the patch?
Cheers, and thanks.

---

### Post by gdselzer on 2008-01-30
If you are using Gutsy and truly have rev 02 of the card then the native drivers will NOT work.  Patching the Hardy kernel is proving to be less than easy (for me at least).  You must use ndiswrapper and follow the guide linked in eggfoo's post above.  Use step 2a (for rev 02) and it should work.

---

### Post by koobert637 on 2008-01-30
I am using the firmware that was installed when I installed b43-fwcutter, a post-install script grabbed it for me but I am using debian sid so it may be different for you all (I hang around here mostly  because of the excellent community :) )

i believe it is the one located at [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

building the kernel is not a big deal, you can just grab the vanilla sources from kernel.org and patch them with this command in the top level source directory

cat (path to patch file) | patch -p1

then use the kernel-package tool make-kpkg to make nice debs for it, there is a tutorial for the whole process at [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

with the new 2.6.24 kernel ndiswrapper is not needed, and actually i couldnt get it to work with 2.6.24 for whatever reason. however the new b43 driver with this patch is working fine

---

