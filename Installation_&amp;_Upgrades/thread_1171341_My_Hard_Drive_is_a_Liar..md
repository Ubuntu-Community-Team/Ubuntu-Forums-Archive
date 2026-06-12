---
title: "My Hard Drive is a Liar."
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Ubi Grimm on 2009-05-27
Recently I was trying to uninstall Ubuntu on my laptop that is dual booted with XP.  I booted the XP disc in recovery mode and did fixboot and fixmbr. This got rid of grub and I was able to then delete the Ubuntu partitions from within windows.  Afterwords I booted the Gparted live disc so I could extend the XP drive to my full capacity. When I went to extend the partition it ran into an error because I hadn't properly shut down windows before booting Gparted. So it told me it couldn't expand the partition but when I hit OK it appeared to have expanded it anyway. I thought to myself "ok whatever" and restarted windows. But then I noticed that when I booted Windows, the windows partition manager (as well as Gparted) says I have a 150gb capacity (which I know is correct). But if I right click my hard drive under My Computer and click properties, it says my capacity is about 133gb. That sounds to me like somewhere in all of this mess the computer forgot where the now blank Ubuntu partitions went. Any help?

---

### Post by cyanics on 2009-05-27
try going to you Computer Management, and Disk Management.

The partition space should be listed as a blank partition, and not included in the running total of space in XP.

if that doesn't work, then reboot into a gpartd boot disk and try to verify that the available space is there.

otherwise, you may have to delete and reinstall everything (including windows) since your master partition records have become corrupted.

---

### Post by Ubi Grimm on 2009-05-27
I actually booted into the G-parted live cd again, right-clicked the partition, and clicked "check". It already was showing itself on G-parted as a capacity of about 150gb (the correct capacity) but I ran the check anyway. Turns out the problem is fixed! The only problem now is that I can't run a disk check or defrag in windows. But it's telling me that chkdsk is scheduled to run, so I will restart now and post results. Thanks for your help!

---

### Post by Ubi Grimm on 2009-05-29
I've run into another problem now. I was able to run chkdsk, although I had to do it from the Windows install disk. But when I run chkdsk, it then starts to tell me again that I have the smaller 133gb capacity, which is incorrect. I can run check on Gparted again and get the capacity back but then I can't run disk check or defragment in windows, so something is still wrong.

---

