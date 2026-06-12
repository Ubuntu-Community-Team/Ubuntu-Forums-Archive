---
title: "External Harddrive not recognized"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by WhisperBlade on 2007-04-09
Hello Forums:

My external harddrive is USB, plugged in, powered on, but not recognized. My Ubuntu 6.10 simply does not recognize it. No icons, no signs, nothing. Any idea why this might happen, and how I can fix it? 

The Ext. USB HD is NTFS format. 

Thanks.

---

### Post by sam81 on 2007-04-09
I'm not sure, it might be because it's in NTFS format, wich is not yet fully supported by default. You should install and look for info on the ntfs-3g driver before trying to write on that HD.

Said that, if the drive doesn't show up automatically try mounting it manually

pmount -t ntfs /dev/yourdevlabel /home/yourusername/flash/

for the device label try to see the output of dmesg (at the bottom) after plugging the HD, it should be something like sdb or sdc

---

### Post by dbansal on 2007-04-10
I too am having the same problem. I have a venus ds3 enclosure with a SATA 250gb HD on an NTFS file system.

This is what i get when i put the following commands:

[I]sudo fdisk -l
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         319     2562336   82  Linux swap / Solaris
/dev/hda2             320         956     5116702+  83  Linux
/dev/hda3             957        7297    50934082+  83  Linux
lodge@lodge-server:~$ 
[/I]

also when I do dmesg i get this:
[I]
[109152.182434] usb 2-2: new full speed USB device using uhci_hcd and address 7
[109152.325707] usb 2-2: configuration #1 chosen from 1 choice[/I]

I am a total n00b. I just recently installed ubuntu on my desktop. I used this external on my Windows Xp laptop.

Also, when i go into system > administration > device manager the system does detect something. However, this is what it says: Unknown (0xffff). Also, Under the vendor specifications it does detect that it has an Oxford chipset.

Any ideas?!

THANKS!

---

