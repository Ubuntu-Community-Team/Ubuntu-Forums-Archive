---
title: "The module that won't die"
date: 2008-07-31
forum: Hardware
---

### Post by Xenoguy on 2008-07-31
So, i have most of my system up and functioning perfectly.  I have to say, great community support you've all been very helpful.  I'm running ubuntu 8.04 32 bit.

Today's problem is that I can't seem to stop a kernel module from loading.

I've tried adding a line to /etc/modprobe.d/blacklist with no luck.

I've tried deleting the module from /lib/modules/kernelversion and then running depmod -a with no success.

The module in question is sata_mv.  it simply doesn't work right, and i want to use the manufacturers driver which does work, and has worked in ubuntu 7.x (Highpoint Sata RocketRaid 2310).  if i load both modules, they conflict and everything goes badly from there.

I checked the kernel options, and its compiled as a module, as opposed to directly in the kernel.  seems evident from the sata_mv.ko file in /lib/modules.  so i really can't figure out how it's loading after i delete the file, and have it blacklisted.

I mean, i could compile my own kernel, but it seems like a lot of effort just to get rid of one single module.

Anyone got any ideas?

---

### Post by prshah on 2008-07-31
> **Xenoguy said:**
> 
Today's problem is that I can't seem to stop a kernel module from loading.
I've tried adding a line to /etc/modprobe.d/blacklist with no luck.


the blacklist should work, everytime, no matter how or where the module is loaded. Can you post your /etc/modprobe.d/blacklist file, as well as the permissions on it?

Can you manually unload the module? In which case you can add that command to your /etc/rc.local. Don't disturb the last line in this file.

There are a couple of other places (at least!) where the module can be manually unloaded, but I can't recall off-hand where... maybe later?

---

### Post by Xenoguy on 2008-07-31
here's the contents of my blacklist.  the permissions look ok too.

> -rw-r--r-- 1 root root 999 2008-07-31 18:46 /etc/modprobe.d/blacklist


```
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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist sata_mv

```

I can blacklist other modules without issue.  for instance i blacklisted bluetooth as a test, because i have no bluetooth devices.

I can unload it with rmmod, so maybe the rc.local solution will be an ok workaround.  I guess then i'd just modprobe my other driver in after its removed.

---

