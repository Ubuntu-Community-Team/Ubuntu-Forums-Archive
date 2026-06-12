---
title: "Help!  Move /home to new partition?"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by Blind Tiger on 2007-09-14
I have read several threads and HowTo's about the /home directory and partitioning, but none seem to match my exact circumstance.

I have my /home on it's own partition (hdb4), but I want to move it to a larger partition (sda1) that I was unfortunately not given the option to use during install (I would have had to reformat the entire disk and lose all partitions).  After install, I was able to use fstab to mount my sda1 partition to a directory I created /mnt/newhome.  I want to unmount /dev/hdb4 from my /home   and mount /dev/sda1 to /home.

My ./ is mounted to /dev/hdb2.

I have tried to unmount my /home, but I get the error message that it cannot be done because the device is in use.

Any help would be greatly appreciated.

---

### Post by rivalarrival on 2007-09-14
Google is your friend.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

While this is not the EXACT same scenario, it should be close enough to suit your needs.

---

### Post by Blind Tiger on 2007-09-14
Thanks for the reply and link.  I have completed this process inasmuch as mkdir /newhome, copying /home to that new directory after mounting my partition of choice to /newhome, but since I already have /home on a separate partition than root, I think what I have to do is edit fstab to remove that partition entirely from any directory, then recreate a /home (or rename /mnt/newhome to /home) and mount my /sda1 partition to it.  Make sense???!!!

Also, any idea why Gparted doesn't recognize my partitions on sda, but fstab -l sees all partitions on all drives, and I am able to mount and unmount from command line without any error?

---

### Post by logos34 on 2007-09-14
If I understand your situation correctly, all you need to do is take out the UUID and '/dev/hdb4' in fstab for the existing /home and replace with the new:

> /dev/**sda1** /home ext3 ...

Now sda1 will mount as your new /home

hdb4 will no longer mount.  You can of choose to do so by adding a new mount point and fstab entry.

You might want want to put off erasing/formatting sdb4 until you're sure everything is in order.

---

### Post by rivalarrival on 2007-09-15
> **Blind Tiger said:**
> Thanks for the reply and link.  I have completed this process inasmuch as mkdir /newhome, copying /home to that new directory after mounting my partition of choice to /newhome, but since I already have /home on a separate partition than root, I think what I have to do is edit fstab to remove that partition entirely from any directory, then recreate a /home (or rename /mnt/newhome to /home) and mount my /sda1 partition to it.  Make sense???!!!


If you've done this right, you shouldn't be recreating or renaming anything. I think you understand this, but just to prevent any confusion, let me see if I can explain it.

from the filesystem's perspective, /mnt/newhome = /dev/sda1
Any time the file system is told to do something to /mnt/newhome, it understands that it should do it directly to /dev/sda1.

From sda1's perspective, there is no /mnt/newhome - the filesystem stripped this part of the hierarchy before anything transferred to sda1. anything you moved into /mnt/newhome is now sitting in /dev/sda1/ ("/" on sda1) writing FILE to /mnt/newhome writes FILE to /dev/sda1/FILE (more or less - you can't REALLY address hard drives / partitions like this, it's just for illustration)  

Changing the mount point of the partition does nothing to the contents of that partition, it just changes how the file system addresses the files on that partition.

FILE is still at /dev/sda1/FILE, but now /dev/sda1 now we mount sda1 at /mnt/differenthome. FILE is now available at /mnt/differenthome/FILE. Your old mount point (/mnt/newhome) would still exist, but it would be an empty folder. 

If you understand that, you understand why nothing needs to be created or renamed, you simply need to mount the right partition to the right mount-point. Changing your existing fstab entry for /home and rebooting will start your computer with the new partition as your home folder. (provided, of course, that everything is copied correctly)

Let us know how it went!

---

### Post by Blind Tiger on 2007-09-28
Thanks to rivalarrival and logos34 for your advice and explanations.  I had determined that the methods you described were the solution to my situation, but I did not want to proceed for being leary of creating an unrecoverable system file error.  I will edit fstab accordingly and relax and enjoy a problem solved!

---

