---
title: "problems booting up"
date: 2008-10-03
forum: General Help
---

### Post by klambert on 2008-10-03
ok im asking this on behalf of my roommate, he knows nothing about computers and im the one who put ubuntu on his computer because his windows died.

It worked awsome for 2 weeks and then all of a sudden when it goes to boot up it not takes forever and it always does a routine check of drives, and then lists some drives, and it gives me and error:
Error reading block 970801 (attempot to read block from filesustem resulted in short read) while reading directory block.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
         (i.e. without -a or -p options)
fsck died with exit status 4

* An autoamtic file system check (fsck) of the root filesystem failed.  A manual fsck must be performed, then the system restarted.  the fsck should be performed in maintenance mode with the root filestystem mounted in read-only mode.
*  The root filesystem is currently mounted  in read-only mode.  a maintenance shell will now be started.
After performing system maintenance, press control-d to terminate the maintenance shell and restart the system.

thats what all it says then it says 
root@name:~# _ 

and u can type stuff where the _ is.  


or i can press ESC to skip the disk check, and then ubuntu loads, and nothing works everything shows up as normal but nothing really works

---

### Post by nitecon on 2008-10-03
Try running fsck when it gives you the option to type stuff.  It sounds like the hard drive on that computer might be going bad.

---

### Post by klambert on 2008-10-03
hehe i forgot to add that my other roommate (not the brightest in the world and weighs well over 250...stepped on his laptop, thats what i figured too btw, was the HD was going bad.

---

### Post by directcharitycontribution on 2008-10-05
i got a thing where the fscking prevents getting to the boot.

then going to boot menu, selecting normal boot, then recovery mood runs against.

hope to find some remedies for more valuable time.

---

### Post by Nielsoerbaek on 2008-10-06
Let me see if i got this right, 'cause i have the same problem. But does this mean my HD is going haywire? But if it is i have to return it on the warranty. But my system works fairly fine if i skip the check. Can i disable it somehow?

---

### Post by directcharitycontribution on 2008-10-08
> **Nielsoerbaek said:**
> Let me see if i got this right, 'cause i have the same problem. But does this mean my HD is going haywire? But if it is i have to return it on the warranty. But my system works fairly fine if i skip the check. Can i disable it somehow?

[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/) says it

try > terminal > man fsck  OR man tune2fs - moderating fsck process ie 1mth instead of 30tim

good configuration described [http://ubuntuforums.org/showthread.php?t=590123&highlight=change+fsck+frequency](http://ubuntuforums.org/showthread.php?t=590123&highlight=change+fsck+frequency) AND [http://ubuntuforums.org/showthread.php?t=553662&highlight=change+fsck+frequency](http://ubuntuforums.org/showthread.php?t=553662&highlight=change+fsck+frequency)

ALSO [http://ubuntuforums.org/search.php?searchid=49237008](http://ubuntuforums.org/search.php?searchid=49237008)

[http://ubuntuforums.org/tags.php?tag=fsck](http://ubuntuforums.org/tags.php?tag=fsck)

[http://ubuntuforums.org/showthread.php?t=300477&highlight=change+fsck+frequency](http://ubuntuforums.org/showthread.php?t=300477&highlight=change+fsck+frequency)

also>  man-fstab

---

