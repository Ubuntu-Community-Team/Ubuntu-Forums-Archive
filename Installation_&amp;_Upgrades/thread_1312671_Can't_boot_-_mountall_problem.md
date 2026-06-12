---
title: "Can't boot - mountall problem?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by subuta on 2009-11-03
Hello,

I have seen other threads discussing some similar issues, but I don't think they are as severe as what I am experiencing, and have not been able to find or follow an appropriate fix.  

I allowed an automatic upgrade to 9.10 (I think) to proceed.  Sometime later, perhaps after the upgrade completed or perhaps when it was still in progress, all of my programs froze but the cursor continued to track the mouse.  I power-cycled the box and now cannot boot.  The error message I am getting is:

One or more of the mounts listed in /etc/fstab cannot yet be mounted: (Esc for recovery shell)
/: waiting for /dev/md3
/tmp: waiting for UUID=<long hex code of some kind>
.
.
and so on for all of my filesystems

When I switch to the recovery console I get:
mountall: Cancelled
init: mountall main process (981) terminated with status 1
General error mounting filesystems

I would greatly appreciate some help getting my system to boot again.

Many thanks.

-Dan

---

### Post by subuta on 2009-11-03
This problem is solved.  I mounted the root filesystem from the recovery console and completed the installation witk dpkg, the same procedure that another member had documented.

---

### Post by KFwLsKvVAs on 2009-11-03
could you detail the steps you had to take to do this or link to the other thread you found how to do it?  I'm having the exact same problem.

---

### Post by subuta on 2009-11-03
It was something like this:

Esc                      to enter recovery shell
mount -a                 to mount all of the devices in /etc/fstab
mount -o remount,rw /    to make the root dir writeable
dpkg -configure -a       (or something like that) to resume the upgrade

---

### Post by blk97tt on 2009-11-04
The following commands resolved the problem for me:

Press esc to enter recovery shell 

fsck

mount -n -o remount,rw /

dpkg --configure -a


Ubuntu was able to boot up after this.  I ran updates through Synaptic and everything appears to be working fine.

---

### Post by Igor80 on 2010-07-23
> **blk97tt said:**
> The following commands resolved the problem for me:
 
Press esc to enter recovery shell 
 
fsck
 
mount -n -o remount,rw /
 
dpkg --configure -a
 
 
Ubuntu was able to boot up after this. I ran updates through Synaptic and everything appears to be working fine.
 
I got this error after trying blk commands:
 
dpkg: parse error, in file '/var/lib/dpkg/available' near line 32464 package 'language-pack-de':
newline in field name ''.'
 
Can anyone help?

---

