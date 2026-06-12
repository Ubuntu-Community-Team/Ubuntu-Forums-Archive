---
title: "Still no love: 9.10 64-bit final does not finish boot on Parallels 4.0.x for Mac!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jonnywot on 2009-10-29
I've tried to post this, with regard to both the beta and the RC of 9.10 64-bit, but it seems to have been left unresolved.  Even while the developers have their hands full rolling out the final and thus acknowledge that they may not get to the forums, so we should post to their beta feedback thread, THAT doesn't seem to have reached anyone.

Now it seems that the 9.10 64-bit final STILL fails to find the media it should be booting off of in Parallels 4.0.x on the Mac.  It doesn't matter if it's a clean install, or an update from 9.04.

Only a hint of this behavior is mentioned by VMWare 2.0.5, as it has trouble finding the IDE host, but then continues and works fine.  VirtualBox 3.0.10 has no problem with it whatsoever.  Also, the 32-bit version of 9.10 (beta, RC or final) shows no trouble with this.

What's going on in Parallels, and is it an Ubuntu or a Parallels problem?  Any suggestions about how to get it fixed?

---

### Post by hrunting on 2009-10-31
I am having this same problem.  I upgraded from a fresh install of 9.04 to 9.10 64-bit in Parallels.  After the reboot, the system goes through grub and then reaches the point where it's trying to find the hard disk, fails and drops me to initramfs.  The error on the screen is:

```
Gave up waiting for root device.  Common problems:2c0daa2f507
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/d824ebf5-d609-491f-aace-32c0daa2f507 does not exist.  Dropping to a shell!
```

In the shell, I can't find any evidence at all of the hard drive.  9.04 64-bit worked just fine.

---

### Post by theteju on 2009-11-03
I have the exct same problem with fresh install 9.10 64 bit on inspiron 1420.

Every thing was working great until I installed,, cairodock and set some desktop graphic effects.

reinstalling grub from community document for GRUB 2 did not help...

Please post the solution soon,, this is really fustrating..

Thanks..

---

