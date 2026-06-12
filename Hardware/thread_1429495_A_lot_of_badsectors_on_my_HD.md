---
title: "A lot of badsectors on my HD"
date: 2010-03-14
forum: Hardware
---

### Post by mlodex on 2010-03-14
Hi there!
I have a HP6720s laptop with 120GB Hitachi harddrive, and recently after installing ubuntu, system greeted me with message that my HD has a lot of badsectors (720 051 to be precise) .. I've read a little about the issue, and i know that hd has the ability to transparently 'remap' unusuable sectors to some hidden reserved space. 

Is it possibile that all of the bad sectors had been remaped? Because when I boot from a livecd, and do on all of my partitions:
```
  fsck.ext2 -v -c -c /dev/sda1
  fsck.ext4 -v -c -c /dev/sda2
  fsck.ext4 -v -c -c /dev/sda3
  fsck.ext4 -v -c -c /dev/sda5
  mkswap -c /dev/sda6
```
like manpage says:
```
       -c     This option causes e2fsck to use badblocks(8) program  to  do  a
              read-only  scan  of  the device in order to find any bad blocks.
              If any bad blocks are found, they are added  to  the  bad  block
              inode  to  prevent them from being allocated to a file or direc&#8208;
              tory.  If this option is specified twice,  then  the  bad  block
              scan will be done using a non-destructive read-write test.

```

It says that none badblocks were found. Could you tell me please how 'fast' those badblocks can spread across the hd? 
Is replacing the hd is my only option?

---

### Post by subedistra7 on 2010-03-14
its a bug, lots of people get the same thing. 

just ignore it.

---

