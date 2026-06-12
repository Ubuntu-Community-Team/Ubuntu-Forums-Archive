---
title: "One particular SD card does not automount"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by psiklotron on 2007-11-27
I have a built in SD card reader. It reads most SD cards fine. I plug them in, they show up on the Desktop and I can work with them. They are mounted to /media/disk. However, I have a 1 GB SD card that behaves differently. It never shows up on the Desktop as an SD card and is mounted to /media/mmcblk0p1/ automatically if it was already in the slot when the computer starts up. The only thing different might be that this card was in the slot when I was installing Ubuntu. I can mount and umount it only as root. 

I have tried removing 'usefree' from gconf-editor -> devices -> vfat but as expected, it didn't change the behavior. It seems to me that for some reason this particular card has been associated as a separate partition or something? This is the extent of my knowledge, any tips on how to proceed to make it behave like a normal SD card?

My system is an HP Presario V2000; Ubuntu 7.10

p.s. Yes, I did go through all the automounting posts, this one seems different because it affects only one particular card. Any tips appreciated. Could the filesystem on this card be different? It shows up as vfat so I dunno if something else could be different? :(

Edit:
I tried sudo mount /media/mmcblk0p1 without the SD card in the slot (and with a different SD card in the slot) and got the following message
"mount: special device /dev/disk/by-uuid/E0FD-1813 does not exist"
This makes me sure(er) that it is marked as a 'special device' in some way. How can i un-special it?

---

### Post by psiklotron on 2007-11-27
Okay, fixed. The device was listed in my /etc/fstab file. I just commented the line listing that device and it worked after i unmounted it. No need to restart.

I could delete this post but I thought I should leave it here in case someone faces the same problem.

---

### Post by larstorben on 2008-02-27
> **psiklotron said:**
> Okay, fixed. The device was listed in my /etc/fstab file. I just commented the line listing that device and it worked after i unmounted it. No need to restart.

I could delete this post but I thought I should leave it here in case someone faces the same problem.

All I can say is, thank you for not deleting the post. It came up high on Google and solved my problem right off the bat.


Thanks again,

Torben

---

### Post by benvantende on 2008-07-09
tHNx saved my day too.

gRTz

ben

---

