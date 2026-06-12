---
title: "Hey, i think my OS's are sick..."
date: 2008-05-23
forum: Hardware
---

### Post by test for echo on 2008-05-23
Hey, i use two OS's, linux ubuntu 8.04 and MS VISTA.
while working is VISTA after a few minutes I get that notorious blue screen with an error message followed by a reboot.

when i work in linux sometime applications don't start up.
my guess that its a partition issue.


> fdisk -l returns like this:
Device Boot Start End Blocks Id System
/dev/sda1 * 1 2946 23661568 7 HPFS/NTFS
/dev/sda2 3892 38914 281312256 7 HPFS/NTFS
/dev/sda3 2947 3844 7213185 83 Linux
/dev/sda4 3845 3891 377527+ 5 Extended
/dev/sda5 3845 3891 377496 82 Linux swap / Solaris

and when i try to run fsck it write down an error message:


> sck 1.40.8 (13-Mar-2008 )
fsck.ext3: Unable to resolve 'UUID=4ea5946f-ca6f-47a4-b05d-48d778e342da'
any suggestions?

---

### Post by BlackDragonBE on 2008-05-23
Everythings seems normal to me, I get the same things. I also dual-boot Ubuntu & Vista by the way.

Start those applications that don't start up in a terminal and post the errors it gives. That will give us more information.
In Vista, could you write down the error message on the blue screen?

Cheers

---

### Post by test for echo on 2008-05-23
ill reboot to VISTA , and turn back with an answer.

---

### Post by ugm6hr on 2008-05-23
> when i work in linux sometime applications don't start up.

Which applications?

How do you launch them?

As explained - try using Terminal - if you don't know how - just tell us the apps, we can tell you how to launch in Terminal.

Also - which version of Ubuntu do you use?

---

