---
title: "Serious problems :("
date: 2005-11-14
forum: General Help
---

### Post by sevenrechlin on 2005-11-14
The other day I was in the middle of copying things from my windows xp hard drive to my ubuntu hard drive (using "Ext2IFS_1_10a") when windows suddenly crashed and rebooted.  Now when I try and start ubuntu I get the following error:

-----------------------------------------
Entry '__init__.py' in /usr/lib/python2.4/brddb (7342352) has an incorrect filetype (was 7, should be 1).

/: unexpected inconsistancy; Run fsck manually (i.e., without -a or -p options)

fsck failed.  Please repair manually and reboot. Please note that the root file system is currently mounted read-only.  To remount is read-write:

# ount -n -o remount,rw /

control-d will exit from this shell and reboot the system.

bash: lesspipe: command not found
bash: discolors: command not found
------------------------------------------

I've tried remounting and restarting, but I keep getting the same error.  Windows can still read-write the drive, so don't understand why.  And if I run fsck it comes up with hundreds of things it wants to fix and many it wants to put in lost+found which doesn't sound like a good thing.

Any advice would be appriciated!  Don't know if it's too messed up, but really don't want to have to start over (yeah I know, it's only been like 2 days!).

---

### Post by Remmelas on 2005-11-15
i've never had good luck with ext2 drivers in windows, last time i used one, it was to fix my grub.conf to match new partitions i set up in partition magic, corrupted enough that fsck had to run, and fix.  I didn't seem to lose anything, even though it dumped a bunch of stuff into lost and found, but I'm not sure you have much choice but to let fsck work it's magic, and hope you don't have to reinstall.

---

### Post by sevenrechlin on 2005-11-15
Well I did it, and things _seem to be_ running just fine :)  Hopefully all that was screwed up was what I was copying, though that python2.4 lib I know had nothing to do with it....

---

