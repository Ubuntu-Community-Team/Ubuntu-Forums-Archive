---
title: "Windows won't load external drive anymore.  Ubuntu still works."
date: 2009-07-22
forum: Hardware
---

### Post by elustran on 2009-07-22
I have a terabyte Western Digital USB HD that I was backing up to from both my Windows machine and from my Ubuntu machine, but after I used my Ubuntu machine to load data onto it and delete and manage some of the data I loaded onto it in Windows, my Windows box no longer sees it - the external devices dialog seems to hang and I can't get into the disk management admin tool.  When I unplug it, everything seems to work properly.  It works fine in Ubuntu.

The external drive came default with FAT32 and some kind of autorun software - I did not reformat.

I'd appreciate any suggestions.

---

### Post by GoldenSun on 2009-07-22
you have to unmount the drive in ubuntu before you can put it back into a windows environment.  

```

sudo unmount /dev/sdx

```

find out what drive it is from gparted or some other way.

---

### Post by biyouboogie on 2009-07-22
I have the same problem, but it's a Vista problem period.   Mine is a Seagate FreeAgent 1TB external and connects USB.  My XP system will see the drive and I can access my files.   Vista will see a device and assign it a drive letter but no longer identifies it as a FreeAgent (the volume label), and if I try to access the drive in ANY way it locks the system and I have to reboot.  

I also had the same problem in reverse.   When I would shut down Vista, the drive would remain marked as "in use" by Vista and Ubuntu could not access it.   Vista simply doesn't unmount the drive.   The only way I could get it to work in Ubuntu was to "Safely Remove Device".   Vista should do that when the system shuts down.    Anyway, I seldom boot Vista anymore because it simply SUCKS.   And... I can not use my 1TB storage on Vista, so why bother even using it?

As for unmounting the drive in Ububtu (and the correct unmount command is...   sudo umount /dev/sdx0    not unmount), there's no reason why you can't simply right-click on the storage device as it appears on your desktop, then select "Unmount Volume" instead of going into a terminal window to accomplish the same thing.   The GUI passes the appropriate shell command to the Operating System.   That's why we have GUI interfaces.

AS for a fix. I think it has something to do with the USB buss and assignment of the appropriate channel, ID, etc.   My thoughts would be Ask the Windows guru at Microsoft, but I will try anything that sounds reasonable to fix the problem... if someone really knows what's causing the problem.    VISTA SUCKS!!

---

### Post by elustran on 2009-07-22
I feel stupid.  I tried the drive on a different Windows machine, and it worked, so, on my own computer, I simply tried waiting for a while to see if the drive would ever unlock.  Well, guess what?  It worked.  All I had to do was wait a few minutes longer.  I think it was taking extra time because my USB 2.0 drivers don't seem to work right.

Today's score:

Ubuntu: 1
Windows: 0

biyouboogie: Good luck with Vista.

---

