---
title: "Why Is Ubuntu So Poor At Multitasking?"
date: 2008-07-19
forum: General Help
---

### Post by Bosconian on 2008-07-19
In Windows, if I run Virtualbox and create a new 8Gb virtual hard drive, I can happily browse the web (or whatever else) while Virtualbox gets on with creating the 8Gb file on my drive.

If I do the same in Ubuntu, the OS grinds to a halt. If I try and access Firefox and view a webpage the screen greys out and it is painfully slow even if it ever comes up at all.

I tried creating this thread while Virtualbox was creating a new 8Gb virtual drive for me (so I can try out openSUSE) and I actually had to give up and wait for Virtualbox to complete. I don't have to do that in Windows.

Maybe I am missing something that I need to install to better support my processor (a Core 2 Duo). Yeah that's right. I'm running Ubuntu on a processor with 2 cores and yet it still refuses to multitask properly.

---

### Post by luke9511 on 2008-07-19
do you have enough ram? cause thats something else you need to have everything run good besides just a dual core

---

### Post by Vivaldi Gloria on 2008-07-19
> **Bosconian said:**
> In Windows, if I run Virtualbox and create a new 8Gb virtual hard drive, I can happily browse the web (or whatever else) while Virtualbox gets on with creating the 8Gb file on my drive.

If I do the same in Ubuntu, the OS grinds to a halt. If I try and access Firefox and view a webpage the screen greys out and it is painfully slow even if it ever comes up at all.

I tried creating this thread while Virtualbox was creating a new 8Gb virtual drive for me (so I can try out openSUSE) and I actually had to give up and wait for Virtualbox to complete. I don't have to do that in Windows.

Maybe I am missing something that I need to install to better support my processor (a Core 2 Duo). Yeah that's right. I'm running Ubuntu on a processor with 2 cores and yet it still refuses to multitask properly.

This has got nothing to do with multitasking. It's about disk writing. I guess you are creating the disk on the same partition that ubuntu lives and so it slows it down. 

Also why don't you use dynamic sized disks?

---

### Post by Bosconian on 2008-07-19
> **Vivaldi Gloria said:**
> This has got nothing to do with multitasking. It's about disk writing. I guess you are creating the disk on the same partition that ubuntu lives and so it slows it down. 

Also why don't you use dynamic sized disks?


Yeah but I can do the same on Windows with no problems at all. On the SAME partition. So why does Ubuntu struggle so badly? And I mean REALLY badly. Windows doesn't.

Oh and to the previous poster, I have 2Gb of RAM.

---

### Post by Vivaldi Gloria on 2008-07-19
> **Bosconian said:**
> Yeah but I can do the same on Windows with no problems at all. On the SAME partition. So why does Ubuntu struggle so badly? And I mean REALLY badly. Windows doesn't.

Have you tried making a vbox disk in the windows partition and running windows at the same time?

What type of partitions are they on? How about the result of

```
sudo fdisk -l
```

---

### Post by Lord DarkPat on 2008-07-19
The filesystem makes a big difference to me. XFS is fastest IMHO, ext3 is fine...and Resier is just..slow

---

### Post by warp99 on 2008-07-19
Most likely because the system is giving a high priority to create the 8GB virtual file so more resources are allocated to VirtualBox. You can nice or renice the VirtualBox app to correct this if it's a problem.

---

### Post by spupy on 2008-07-19
> **Bosconian said:**
> Yeah but I can do the same on Windows with no problems at all. On the SAME partition. So why does Ubuntu struggle so badly? And I mean REALLY badly. Windows doesn't.

Or maybe it's VirtualBox' fault? Even if it the "same" program, it is a virtual machine that has a lot of OS specific code, so it is expected to act differently under Windows and Ubuntu. Don't always blame poor driving skills on the car!

---

### Post by Flyingjester on 2008-07-19
> **warp99 said:**
> most Likely Because The System Is Giving A High Priority To Create The 8gb Virtual File So More Resources Are Allocated To Virtualbox. You Can Nice Or Renice The Virtualbox App To Correct This If It's A Problem.

+1

---

### Post by Vivaldi Gloria on 2008-07-19
I think it's more about the space left on the partitions. If the ubuntu partition has less space and it's ext3 then it'll move a lot of files around to minimize fragmentation.

But ntsf doesn't care about fragmentation at all. That's why ntsf partitions require frequent defragmentation.

But we can end this guess-work with an output off

```
sudo fdisk -l
```

---

### Post by Bosconian on 2008-07-19
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49cf544f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2794    22442773+   7  HPFS/NTFS
/dev/sda2            2795       14593    94775467+   5  Extended
/dev/sda5            2795       14107    90871641   83  Linux
/dev/sda6           14108       14593     3903763+  82  Linux swap / Solaris

---

### Post by Vivaldi Gloria on 2008-07-19
That doesn't show disk usage of course. Can you please also post

```
df -h
```

---

### Post by Vivaldi Gloria on 2008-07-19
I'm going to sleep. Before that let me make a last comment. There is no problem in linux's multitasking. This is completely something about partitions and filesytems. They are on different partitions with different filesystems. So you are comparing apples and oranges. I remmember reading that ext3 copies slower than ntfs. Maybe this is somewhat related. They are very different filesystems with different goals. So to make a fair comparision you should consider tests on similar filesystems.

To solve your practical problem, use dynamically expanding images rather than fixed size ones.

Goodnight everyone.

---

