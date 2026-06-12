---
title: "install problem, root disk does not exist, initramfs"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by kazmo on 2009-07-08
Installing Ubuntu over Windows XP on a windows XP box using the latest ISO of 9.04, downloaded July 4th.  The hardware is a Dell, Intel P4 at 1.6Mhz.  The box has two IDE drives, one 250Gig, one 40gig.

The 250 gig drive is seen by XP as the C: boot drive, and by the BIOS as Drive 0.

The installation appeared to go smoothly.  I choose to load Ubuntu to the C: drive.  Upon booting Ubuntu, I received the message:
************************************
```
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```
************************************

Searching the forums turned up a number of similar problems.  The one that sounded most similar involved adding "rootdelay=90".  

I tried all of those things. That wasn't it.

Booting back into XP and looking at the drives showed the wubildr, boot.ini and config files had been copied to both the C: and E: drives.  The Ubuntu directory was on the c: drive, which is what I expected.

So reboot back to Ubuntu.  At the Busybox shell, I tried to find a directory that existed on the C: drive.  Nothing found.  I thend tried a find on a files that existed only on the E: drive, and low and behold, there it is.  So Ubuntu was looking for the root.disk on a drive different from the one specified to WUBI in the install process.

I was luck enough to have allocated only 20gb to Ubuntu during the install.  Since the E: drive had enough space available, I copoed the Ununtu directory over from C: to E:.

Sure enough, Ubuntu booted after that change.  After plinking around and creating a couple of test files, I dropped Linux and re-booted XP.  The root.disk on the E: drive had been updated, the root.disk on C: still had the date/time stamp from the install.

Question:
1) Is this a known issue?  It sounds similar to other problems, but those solutions did not resolve the issue.

2) I figure I could pull the plug on the E: drive and re-install.  Is there another easier fix?  It dual boots fine, I'd just as soon not mess up the XP install.

3) If it sounds like a new bug, what is SOP for reporting it?  There's so much stuff to read, I must be searching for the wrong things.

---

### Post by short circut on 2009-07-08
It seems to be a known problem. I am having the same issue, but since I didnt use wubi i cant do much to fix it unless someone has a suggestion

---

### Post by short circut on 2009-07-09
Ok so after several hours of work I have found a full solution to this problem. This works best on physical installs, not sure about wubi.

Instructions
1)boot into a live cd's recovery mode. Don't bother trying to mount anything it wont work.
2) first run lvm vgchange --ignorelockingfailure -P -a y 
3) the output of this will have a title like the computer name in quotations. Note this title. from now on referred to as title
4) next run lvm vgmknodes
5) This will create a block device of the logical volume in question.
6) run fsck -n /dev/title/root
7) of course replace title with the appropriate string. If this actually runs you are in business. Let it finish out. It may take a while.
8) finally run fsck -f -y /dev/title/root

this will take time, but it will work. It will replace the superblock with one of the backups, and it will clean the filesystem. finally reboot to an again working  system.

The fixes to this problem are not well documented. It would be nice if someone added this fix to some sort of manual and google bombed it to the top of the search so no one has to go through this frustration again.

---

### Post by kazmo on 2009-07-09
OK.  Thanks.  

When I cut and paste my original post, I left out the important part.  I'm a real Linux NOOB.

I get the basic drift of your solution using the volume manager.  But without understanding the volume manager and bash commands better, pulling the plug on one of the hard drives and doing a full re-install seems simpler from the noob-ish perspective.  If I get to the point where I understand your solution better, I may experiment.

The install over XP using WUBI seemed to be straight forward beyond the single glich I encountered, and the work-around was not complicated. So currently I'm just using the install with the root.disk on the wrong physical drive.  No ill effects yet encountered.  

It has been years since I took Unix out for a test drive.  So far so good.  There are some specialized apps that will keep me mired in windoze for many moons, but it may be with a second physical box and a KVM switch.  Migrating the mundane uses to Linux seems much more feasible now.

---

