---
title: "Hard drives have different device names after reboot"
date: 2009-02-14
forum: Hardware
---

### Post by ridetheteapot on 2009-02-14
I'm having this problem where sometimes my master sata drive will boot up as /dev/sdb or othertimes /dev/sda (like i would assume).

I usually boot with 1 internal sata, 1 esata, 1 usb, and cdrom and hd on ata. Most of the time it seems to be that the sata and the ide hd (slave to ata cdrom) switch thier device names.

As far as functionality goes, its not really a problem, my fstab uses the by-volume-id to mount the drives correctly, but I'm still really curious to why this happens.

---

### Post by ridetheteapot on 2009-02-17
anybody have an idea?

---

### Post by kpatz on 2009-02-18
I'll add a bump for you...

UUIDs are handy for getting around this for mounting purposes, but if you're using RAID having the drives shuffle themselves on a reboot can kill the array.  So is there a fix for this?

---

### Post by Hefeweiz3n on 2009-02-18
I think the drives get their names assigned in the order that the system recognises them. So if this order changes at startup (shouldn't happen with interal drives, just the external ones) you get different devicenames.

As for the RAID-Setup. I have a Raid5 with 4 Disks running using mdadm and have no problems. recently one of my older drives that was used only for downloading stuff gave up, next restart the drives got different names: no problem, as dmraid doesn't recognise them by their devicenames but by some other method. So no worries, your raid is safe.

---

### Post by kpatz on 2009-02-18
actually, I found some info here: [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

on how to create udev rules to force each drive to have a specific device name.

---

### Post by ridetheteapot on 2009-02-22
hey kpatz are udev working for you? I'm using the default by-volume-id udevs to workaround my problem (as in above post). I have not tried to use udev to assign names like /dev/sda because i am afraid something funny happening in a conflict....
Using udev rules aside from naming sda/sdb etc is not a good workaround because some apps look to the hardrives in set places. (Often I am finding that /dev/disk/by-volume-id/etc is not recognized as a device file by some programs). But am not using a raid, so well guess thats lucky :)

Also I am positively defiantly having swaps between internal drives (sata<->ide, but also my sata<->esata)

Stating to think its my bois more then anything

---

### Post by ridetheteapot on 2009-03-09
I have to bump this. If anyone has an idea please post.
It is defiantly linux and not my bios.
While grub is using uuid's to boot, i works fine by hd position (ie. hd 0,2).

I am not looking for a workaround (sometimes i think thats all you can get off ubuntuforums), I am trying to figure out why.

---

### Post by Nullexe on 2009-09-15
@ridetheteapot have you had any more luck with this?  The same thing happens to me when I install a new drive or sometimes randomly....

I have a lvm raid5 setup for my data, when I manage to get the drives back in the right order I can recover but why do the device names change in the first place??

---

