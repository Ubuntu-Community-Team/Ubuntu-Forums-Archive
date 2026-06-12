---
title: "Why doesn't ESATA work??"
date: 2008-08-05
forum: General Help
---

### Post by davidw89 on 2008-08-05
Any ideas on how to fix this?? It normally works fine in Windows
[[IMG]http://img255.imageshack.us/img255/9479/screenshotnt7.png[/IMG]](http://imageshack.us)
[[IMG]http://img255.imageshack.us/img255/9479/screenshotnt7.3d73835121.jpg[/IMG]](http://g.imageshack.us/g.php?h=255&i=screenshotnt7.png)

---

### Post by davidw89 on 2008-08-05
[[IMG]http://img299.imageshack.us/img299/3991/screenshot1im0.png[/IMG]](http://imageshack.us)
[[IMG]http://img299.imageshack.us/img299/3991/screenshot1im0.a07582cc9d.jpg[/IMG]](http://g.imageshack.us/g.php?h=299&i=screenshot1im0.png)

---

### Post by articpenguin on 2008-08-05
Try booting into windows and let windows replay the ntfs logfile it does this at bootup. Then boot back into ubuntu and see if it mounts.

---

### Post by davidw89 on 2008-08-06
I don't have Windows isntalled...

I did a clean install of Ubuntu

Is it possible to install Windows XP (dual boot) when you have linux installed first?

---

### Post by davidw89 on 2008-08-06
Sigh usb dont work either wtf

---

### Post by Nepherte on 2008-08-06
First off, try to resize your pictures in the future. The disk is not properly unmounted. Most of the times, it's because you simply unplugged it without unmounting it first in Windows. Most of the times you can simply fix it by attaching it to a Windows computer and unmount it correctly ("safely remove hardware icon" in windows).

---

### Post by davidw89 on 2008-08-06
But it was never plugged into windows :/

---

### Post by mcduck on 2008-08-06
The drive is recognized as NTFS drive that has been removed from computer without ejecting it properly.

If it really _is_ NTFS, then you need to plug it in to a Windows system and then eject correctly.

If the file system is not NTFS, but something else, post here putputs of "Sudo fdisk -l" and "cat /etc/fstab" (while that drive is connected).

And, finally, if the drive is NTFS but you are not using Windows at all you should format it into some Linux-native file system, like Ext3.

---

### Post by davidw89 on 2008-08-06
Yes it's NTFS. Well the problem with ext3 is that networking don't over over Windows OS..

---

### Post by articpenguin on 2008-08-06
well the NTFS partition is marked dirty because it was uncleanly mounted and to prevent corruptions it wont mount. Linux does not have the ablity to fix an ntfs partition yet or replay the journal.

---

### Post by ktechman on 2008-08-06
Was this issue solved?  The outcome would be nice to know. Is there a how-to on E-sata and Ubuntu?

---

### Post by mcduck on 2008-08-07
> **ktechman said:**
> Was this issue solved?  The outcome would be nice to know. Is there a how-to on E-sata and Ubuntu?

It's not an eSATA problem. You get the same issue reagrdless of how the NTFS drive is connected if it isn uncleanly removed.

eSATA should work just like any other SATA connection. It's just a different connector for normal SATA interface.

---

### Post by WinGuru on 2009-02-04
I registered just to clear-up all the MISINFORMATION in this thread.

eSATA IS different from SATA (unlike the previous poster's statement).

To use eSATA, you must be in AHCI mode in your BIOS. IDE emulation will not allow access to eSATA. 

To from IDE to AHCI in Vista, go here:
[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

Take note of your existing Start value so you can revert to IDE if you wish.

WinGuru/JW :p

---

### Post by Gizenshya on 2009-02-04
While I can't vouch for the above post (as I have no experience with eSATA on my computer)...

I can say that the message in the images is not the message that is given when an NTFS drive is blocked by the $logfile (unclean shutdown).  So the problem is not with an unclean shutdown or otherwise unresolved $logfile.

I've heard that some eSATA drives must be hooked up at boot in order to be recognized.  In other words, you can try shutting down your computer, plugging in the drive, and then booting up.  I don't know if that helps in this situation, though.

---

### Post by cariboo on 2009-02-04
There is a problem with hot plugging eSata drives, If I have my eSata drive turned on at boot it is recognized, but if I turn it on after boot up it is not recognized until a usb thumb drive is plugged in.

Jim

---

