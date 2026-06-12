---
title: "can i disable acx_pci at boot?"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by MrCheese on 2005-11-19
Hi, I use ndiswrapper to load the M$ drivers for my Ti-ACX111-based wifi card. Previously, under Hoary, I used Linuxant driverloader with no problems. However, under Breezy the acx_pci module is loading at boot & I'm having to

rmmod acx_pci
ifdown wlan0
ifup wlano

and usually 

dhclient wlan0

How do I disable acx_pci loading at boot - I can't find it in any config file, so presumably it's in the initrd. Is running mkinitrd once the acx_pci module is removed  enough to get me going?

Cheers,
Paul

---

### Post by Lambert on 2005-11-19
add acx_pci to /etc/modprobe.d/blacklist

---

### Post by az on 2005-11-19
I thought that the acx driver in Breezy could do everything, including WEP (Big improvement over Hoary).  This is not the case?

---

### Post by MrCheese on 2005-11-21
[QUOTE=azz]I thought that the acx driver in Breezy could do everything, including WEP (Big improvement over Hoary).  This is not the case?[/QUOTE]

TBH I've not really given it a go - I had such major a$$ pain with acx_pci under Hoary that I regard the module just as an evil curiosity. That said, when the laptop boots I don't get any lights on the card. When I rmmod it and ndiswrapper takes over the power light comes on immediately. I may tinker, but as ndiswrapper works I won't spend much time doing so.

Paul.

---

### Post by sadsac on 2005-12-14
I can't seem to stop acx_pci from loading at boot. Here is what I have tried:

As suggested above in this tread, I created the file "blacklist" in /etc/modprobe.d, and added "acx_pci". Rebooted... but acx_pci is still loading (checked using; lsmod | grep acx)

Is /etc/modprobe.d/blacklist the correct location for the blacklist file? There was no existing blacklist file there to start with...

I also tried renaming acx_pci.ko in lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/acx/. Then did;

sudo depmod -a

and rebooted

That didn't work either. Could it be finding acx_pci.ko in the other kernel version?

Also, after searching here, I also tried adding acx_pci to the blacklist at /ect/hotplug/blacklist. Still didn't work, acx_pci is still loading at boot.

Is there a definitive way to disable acx_pci from loading at boot? Thanks

---

### Post by az on 2005-12-14
[QUOTE=sadsac]I can't seem to stop acx_pci from loading at boot. Here is what I have tried:

As suggested above in this tread, I created the file "blacklist" in /etc/modprobe.d, and added "acx_pci". Rebooted... but acx_pci is still loading (checked using; lsmod | grep acx)

Is /etc/modprobe.d/blacklist the correct location for the blacklist file? There was no existing blacklist file there to start with...

I also tried renaming acx_pci.ko in lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/acx/. Then did;

sudo depmod -a

and rebooted

That didn't work either. Could it be finding acx_pci.ko in the other kernel version?

Also, after searching here, I also tried adding acx_pci to the blacklist at /ect/hotplug/blacklist. Still didn't work, acx_pci is still loading at boot.

Is there a definitive way to disable acx_pci from loading at boot? Thanks[/QUOTE]


I think it is hotplug that is loading the module.

/etc/hotplug/blacklist

So, the native driver does not work?

---

### Post by Lambert on 2005-12-14
Some don't have that file set up for what ever reason. Here's what what my file looks like.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


And it's path is /etc/modprobe.d/blacklist

If you didn't have that file I would guess you didn't add blacklist in front of the module.

---

### Post by az on 2005-12-14
[QUOTE=Lambert]Some don't have that file set up for what ever reason.
 ...

If you didn't have that file I would guess you didn't add blacklist in front of the module.[/QUOTE]

The reason is that hotplug is depreciated in Dapper.  It is replaced by HAL and Dbus.

If you are running Breezy, use hotplug's blacklist.  If you are using Dapper, you do not have hotplug.

---

### Post by Lambert on 2005-12-15
Thanks azz, learned something today.

Now I have a question if you can answer.

There are two ways a module is used (from what I understand) You can build it into the kernel base or as a loadable kernel module (LKM)

Can you blacklist a module that's built into the kernel base or just LKM? 
If you blacklist an item correctly based on what distro and version is being used but it still loads, what is happening that the module is still being loaded?

---

### Post by az on 2005-12-15
[QUOTE=Lambert]
There are two ways a module is used (from what I understand) You can build it into the kernel base or as a loadable kernel module (LKM)?[/QUOTE]

Actualy, a kernel option that is built-in to the kernel is a kernel option.  If you build it as a module, then it is a loadable module.  The statically built-in option is loaded along with the rest of the vmlinuz image.  You cannot remove it.



[QUOTE=Lambert]If you blacklist an item correctly based on what distro and version is being used but it still loads, what is happening that the module is still being loaded?[/QUOTE]

Warty used Discover and hotplug to load modules.  The warty live cd even used HW-detect (red-hat kudzu), too.  Hoary wrapped discover into hotplug and the live cd used the same system as the regular install.  Now, hotplug is redundant to hal and dbus.  So everything is being put into that.

Modules do not load automatically.  Something has to load them or another module that depends on them.  Check dmesg to see how the module is being loaded.  I think the other kernel, system and message logs can be more verbose if dmesg is not clear enough.

Some modules are loaded by the initrd.  But those are generally just disk drivers and so forth.  I think the initrd still uses discover.

---

