---
title: "Unable to mount partition"
date: 2008-10-06
forum: General Help
---

### Post by Isoss on 2008-10-06
Hi, I am having a strange problem. 
I have played with the partitioning of my laptop while ubuntu is installed on one partition, and resized some to create a new one for another system.
I did that from live CD using "gparted".
After a free space was created, I moved ubuntu's partition and swap to the right so I can have the empty space on which I wanted to install windows. When I restarted, everything worked fine and I logged in to ubuntu. I rebooted and installed Windows on the free partition. Something went wrong after the first part of windows installation that I couldn't login neither to (continue installing windows nor there was grub) .. so I decided to install DeskTopBSD on the same partition of windows. After that its grub detected ubuntu .. but when I tried to login to ubuntu I received an error in the unix: Error: Unable to mount partition! from DeskTopBSD and live ubuntu CD I am able to see the files of other partitions including ubuntu partition. 

From Ubuntu Live CD I reconvered the ubuntu grub and it DeskTopBSD grub was replaced with ubuntu's but still I get that error.

how can I solve this issue?

Thanks in advance.

P.S, I am have ubuntu 8.04

---

### Post by geirha on 2008-10-06
When in the boot process does that error message show up? Does it show the splash screen with progress bar first etc?

My guess is that the UUID for the filesystem ubuntu is on has changed, and you need to change it in /etc/fstab. Paste the content of ubuntu's /etc/fstab and the output of ```
sudo blkid
``` run from the live session of the ubuntu CD.

---

