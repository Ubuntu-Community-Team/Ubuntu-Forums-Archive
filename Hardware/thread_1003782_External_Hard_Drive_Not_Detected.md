---
title: "External Hard Drive Not Detected"
date: 2008-12-06
forum: Hardware
---

### Post by DocHolliday2006 on 2008-12-06
Hi. I just bought (never used on another computer before) an Acomdata "The Executive" Portable 2.5"  Hard Drive. I connected it to my computer, which has the latest version of Ubuntu installed, via USB. The light on the drive went on, so there appears to be power flowing to it. 

However, nothing pops up on my screen asking me to install the new hardware, etc. Going into computer, I don't see any new drive listed.

How do I install this?

I want to use it for data backup, not a new Ubuntu install.

Thanks,
-Andrew

---

### Post by taurus on 2008-12-06
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
dmesg | tail
```

p.s.  Have you formatted the new drive?

---

### Post by DocHolliday2006 on 2008-12-06
I have not formatted. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f11e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       26754   205133985   83  Linux
/dev/sda3           26755       30401    29294527+  82  Linux swap / Solaris


> **taurus said:**
> Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
dmesg | tail
```

p.s.  Have you formatted the new drive?

---

### Post by ranch hand on 2008-12-06
I probably shouldn't say this but I am glad you have this problem.  I put a IDE HDD in an enclosure and played with the format and screwed it up and now can't detect it.  This thread may help.

The "sudo fdisk -l" did detect the drive and the other command did tell me it is screwed up so I am suprised that you got nothing back.

I hope you get it going.

I am going to fire up my old computer with this HDD installed and see if I can formate it from bios.

Good luck, I subscribed so I can learn more CLI commands.

---

### Post by DocHolliday2006 on 2008-12-07
So does this mean anything to anyone? Any advice?

> **DocHolliday2006 said:**
> I have not formatted. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f11e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       26754   205133985   83  Linux
/dev/sda3           26755       30401    29294527+  82  Linux swap / Solaris

---

### Post by ranch hand on 2008-12-08
That is the hard drive that you are using and the partitions on it.

This is what mine looks like.  The last entry is my external that is not right.

tom@hogwash:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004630f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18209   146263761   83  Linux
/dev/sda2           37778       38913     9124920    5  Extended
/dev/sda3           18210       24583    51199155   83  Linux
/dev/sda4           24584       37777   105980805   83  Linux
/dev/sda5           37778       38913     9124888+  82  Linux swap / Solaris

Partition table entries are not in disk order

Unable to read /dev/sdf

Running "dmesg | tail" then gets me:

tom@hogwash:~$ dmesg | tail
[60238.354896] sd 7:0:0:0: [sdf] Device not ready: Sense Key : Not Ready [current] 
[60238.354904] sd 7:0:0:0: [sdf] Device not ready: Add. Sense: Medium not present
[60238.354910] end_request: I/O error, dev sdf, sector 8
[60238.354913] printk: 1 messages suppressed.
[60238.354915] Buffer I/O error on device sdf, logical block 1
[60238.510372] sd 7:0:0:0: [sdf] Device not ready: Sense Key : Not Ready [current] 
[60238.510379] sd 7:0:0:0: [sdf] Device not ready: Add. Sense: Medium not present
[60238.510384] end_request: I/O error, dev sdf, sector 32
[60238.755200] sd 7:0:0:0: [sdf] Sense Key : No Sense [current] 
[60238.755210] sd 7:0:0:0: [sdf] Add. Sense: No additional sense information


This shows that my box is actually detecting the external but that it is bad.  I do not know how to fix this in my box but I think that I can install the HDD internally on my old box and format in bios and then put it back in my enclosure.

I would like to know if you had your external on for while.  It seems to take a while,  a couple minutes, for my box to see mine this well.

Other than that, I don't know.  I assume that you have checked the usb connection.

Have you tried your external on any other machine?

It sure looks like you really are not in contact with it at all to me but I just started fooling with Ubuntu and linux in August so I am far from knowing what I am up to.

---

### Post by DocHolliday2006 on 2008-12-08
I've left it on for awhile, and it doesn't seem to make a difference. I've checked the USB connection and switched around the port just to be sure. I haven't tried it on another machine. 

Thanks for your help. Anyone else have any insight? 

> **ranch hand said:**
> 

I would like to know if you had your external on for while.  It seems to take a while,  a couple minutes, for my box to see mine this well.

Other than that, I don't know.  I assume that you have checked the usb connection.

Have you tried your external on any other machine?

It sure looks like you really are not in contact with it at all to me but I just started fooling with Ubuntu and linux in August so I am far from knowing what I am up to.

---

### Post by ranch hand on 2008-12-09
I would try it on another machine to make sure that there is not something wrong with the external drive itself.

---

### Post by ranch hand on 2008-12-11
This is just a bump.

I hope someone has some help on this.

I would still like to know if you tried this on another box to see if the thing really works.

---

