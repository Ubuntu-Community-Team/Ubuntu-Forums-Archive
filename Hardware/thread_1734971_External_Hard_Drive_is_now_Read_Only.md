---
title: "External Hard Drive is now Read Only"
date: 2011-04-20
forum: Hardware
---

### Post by SwitchOverride on 2011-04-20
I know there is probably a thread with an answer that would actually help me, but I've been looking for the past hour and haven't found anything that worked.

I have a Western Digital My Passport 320 gig usb hard drive and when I tried to do my weekly backup of my computer in Ubuntu 10.10, it said that the destination folder was read only.  I've tried several different methods of fixing this, such as using the disk utility to find any errors on the disk surface or any bad sectors and ended up with a failed read test in the SMART data test window.  I used the lsusb command as root and got this output.

root@private:/****/******# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b093 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Nothing wrong that I can see, so I tried unmounting it, rebooted, and mounted it again and still got the same error.  I know some people will think that it must be formatted NTFS for windows or as a win32 format, but I guarantee that it is formatted in FAT32 format, because before I put anything on it and started using it, I personally formatted it using PE2USB.  Also, disk utility says that it has about 8 bad sectors, so I tried using a friend's computer with some sort of crap Windows install to try and recover those sectors and it did without data loss.

I have over 180 gigs used already because of all the OS iso's that I have for my pc support classes and my personal information and files and nowhere large enough to store all of it so I **REALLY** don't want to try reformatting it.  If there is anyone who has an idea of how to fix this issue, please tell me.  I'm a native Linux user and have only used that crap Bill Gates calls an OS for the few programs that needed an NTFS system to run or install, so if anyone can help with this first time problem, I would appreciate the help.

Switch.

---

### Post by brpylko on 2011-04-20
If you have a mac try running disk utility, I think there is a setting in there that windoze may have screwed up in repairing the sectors.

---

### Post by SwitchOverride on 2011-04-20
I forgot to mention that before I started having this problem, I did make it bootable as a multipass like my Sandisk pendrives.  I doubt that that would be the problem, but I just wanted to add that.

---

### Post by brpylko on 2011-04-20
Is it possible that windoze "repaired" the boot sector *thinking *it was broken?

---

### Post by brpylko on 2011-04-20
actually, the easiest thing to do would probably be this:

1. copy files from HD to another location.
2. reformat the external HD.
3. move files back to HD.

---

