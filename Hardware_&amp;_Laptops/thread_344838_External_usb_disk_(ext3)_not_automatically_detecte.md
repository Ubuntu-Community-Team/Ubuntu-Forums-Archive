---
title: "External usb disk (ext3) not automatically detected on boot"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by TomG on 2007-01-23
Hi, 

My external usb disk (ext3) is not automatically detected on boot. I need to unplug and replug it each time.
lsusb seems not see it. Disk manager sees it but says there is no partition.
Is there a way/command that you be ran (automated) to force check of undetected USB devices ?

Thx
Tom

---

### Post by dannyboy79 on 2007-01-23
> **TomG said:**
> Hi, 

My external usb disk (ext3) is not automatically detected on boot. I need to unplug and replug it each time.
lsusb seems not see it. Disk manager sees it but says there is no partition.
Is there a way/command that you be ran (automated) to force check of undetected USB devices ?

Thx
Tom

did you check your configuration in Desktop, Preferences, Removable Drives and Media...


i don't know if this has anything to do with it but my sata drive wasn't being mounted at boot up either. it turned out that when your computer performs the mount all command which parses thru the fstab, my sata driver wasn't loaded yet. so I had to add sata_sis
to my /etc/modules file. maybe there is something similarly wrong with your usb drivers.

this may also shed some light: [http://www.debian-administration.org/articles/127](http://www.debian-administration.org/articles/127)

good luck

---

### Post by TomG on 2007-01-23
Removable Drives settings seem ok. Will check the rest. 
Thanks ! :)

---

