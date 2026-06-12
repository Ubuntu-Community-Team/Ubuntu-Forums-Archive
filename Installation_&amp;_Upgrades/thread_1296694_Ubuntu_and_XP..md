---
title: "Ubuntu and XP."
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by Cityscape on 2009-10-20
I was wondering if it is possible to remove Ubuntu from a dual-boot config?

Reason why I'm asking is cause I'm gonna set my parents up a PC with XP and Ubuntu 9.04 (using GRUB as bootloader) dual-booted. They want to switch to Linux but be able to go back to just Windows if they want.

Is it possible to have them dual-boot and then remove the Linux part and just use XP?

---

### Post by dominiquec on 2009-10-20
Look into your GRUB settings.  It will be in /boot/grub/menu.lst.  Suggestion: don't delete the Linux partition, just set it so that the computer boots to whichever OS, and maybe reduce the timer.

---

### Post by earthpigg on 2009-10-20
for test driving, i suggest WUBI.

if they decide they want to keep it, back up and restore /home on a fresh true-dual-boot-fresh-install to migrate settings.

---

### Post by QIII on 2009-10-20
Yes.  That's not a problem.

I'll spare you the details until you get to that point, if you decide to remove it.

For now...

Have fun with Ubuntu (and tell you parents to as well.)

BACK UP IMPORTANT FILES BEFORE DOING ANYTHING!

Before you start dual booting, though, install XP first.  Makes things easier.  Using two separate physical hard drives is the way to go IMHO.

But if you do it on one disk, defrag a couple of times if XP has been used for a while.  BACK UP IMPORTANT FILES.  (Notice how I wrote that twice in all caps!)

There is a nice tutorial here for dual booting on a single disk:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

Using two separate physical hard drives is similar, except that during the partitioning process you just have to make sure you are putting the Linux partitions on the right device.

Please check back in if you run into any problems before you try to bull through them and wind up with a mess, though.

Welcome.  Happy Ubuntuing!


Edit:  Or use earthpigg's suggestion.  I've never used Wubi, so I can't help you there.

---

### Post by Cityscape on 2009-10-21
> **qiii said:**
> yes.  That's not a problem.
I'll spare you the details until you get to that point, if you decide to remove it.
So it can be done, right?

---

### Post by earthpigg on 2009-10-21
so you are saying it is essential to have solid backups, QIII?

just to clarify.

:D

---

### Post by earthpigg on 2009-10-21
> **Cityscape said:**
> So it can be done, right?

via the easiest and least complex method, you will need to rely on windows tools used in a manner approved by Microsoft to do it....

[http://en.wikipedia.org/wiki/Fixmbr#Invoking_the_recovery_console_from_the_installation_CD-ROM](http://en.wikipedia.org/wiki/Fixmbr#Invoking_the_recovery_console_from_the_installation_CD-ROM)

---

### Post by QIII on 2009-10-21
> **earthpigg said:**
> so you are saying it is essential to have solid backups, QIII?

just to clarify.

:D

Marines need two backups.

---

### Post by Cityscape on 2009-10-21
> **earthpigg said:**
> via the easiest and least complex method, you will need to rely on windows tools used in a manner approved by Microsoft to do it....

[http://en.wikipedia.org/wiki/Fixmbr#Invoking_the_recovery_console_from_the_installation_CD-ROM](http://en.wikipedia.org/wiki/Fixmbr#Invoking_the_recovery_console_from_the_installation_CD-ROM)

As long as it can be done.

---

### Post by cameronedwards on 2009-10-21
im pretty sure you can remove it like a program.

---

### Post by earthpigg on 2009-10-21
> **cameronedwards said:**
> im pretty sure you can remove it like a program.

only if it is a WUBI install.

---

### Post by Bartender on 2009-10-21
> **Cityscape said:**
> I was wondering if it is possible to remove Ubuntu from a dual-boot config?

Reason why I'm asking is cause I'm gonna set my parents up a PC with XP and Ubuntu 9.04 (using GRUB as bootloader) dual-booted. They want to switch to Linux but be able to go back to just Windows if they want.

Is it possible to have them dual-boot and then remove the Linux part and just use XP?

I want to make sure I've got this straight.  The immediate plan is to set up a standard dual-boot, right?  But you're concerned that several months from now they may find they're not using Linux at all, and in that case they might ask you to remove it?

That's pretty straightforward.  You just have to be aware that removing Ubuntu will require reinstalling the Windows MBR.  There are a million posts on that subject.  
I'd suggest creating an extended partition, then installing all of Ubuntu inside that partition.  

If you decide to wipe Ubuntu, have your MBR fix-it tool ready (there are several) and have a partitioning tool, such as a GParted LiveCD, ready.
With your partitioning tool of choice, wipe all the logical partitions from inside the extended partition.  Then you could create a logical NTFS partition, which XP would be able to use for data.  Or you could delete the extended and resize the XP partition, but there's always a risk manipulating a partition with data.
Then be ready to boot from whatever tool you're going to use to fix the Widows MBR.

---

