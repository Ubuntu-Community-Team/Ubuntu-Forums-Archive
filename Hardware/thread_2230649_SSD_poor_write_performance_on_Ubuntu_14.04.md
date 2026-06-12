---
title: "SSD poor write performance on Ubuntu 14.04"
date: 2014-06-20
forum: Hardware
---

### Post by atterdag on 2014-06-20
**_Summary_**
After upgrading from 12.04 to 14.04 the write performance is painfully slow (less than 5MB/s) of both my SSD drives. The read speed is still fine. I've tested with the latest version of System Rescue CD (4.2.0 at this time) to see if was a hardware problem. However the performance of my drives was even better better than using Ubuntu 12.04.

I've also tried to make a fresh installation of Ubuntu 14.04 on a spare SSD drive of mine to see if its because I upgraded from 12.04. But after waiting 4 hours for it to install, I finally lost patience, and stopped the installation.

I'm using the deadline scheduler, but it doesn't matter which one I use. I'm also using the lowlatency kernel, but using the generic kernel doesn't have any effect.


**_Details_**

**Kernel version**
root@ubuntu:~# uname -a
Linux fk20563 3.13.0-29-lowlatency #53-Ubuntu SMP PREEMPT Wed Jun 4 21:20:42 UTC 2014 i686 i686 i686 GNU/Linux

**List hardware**
lshw > [lshw.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/lshw.txt")

**SSD identification, and timings of devices**
root@ubuntu:~# hdparm -I /dev/sda > [/hdparm_sda.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sda.txt")
root@ubuntu:~# hdparm -t /dev/sda >> [/hdparm_sda.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sda.txt")
root@ubuntu:~# hdparm -t /dev/sda >> [/hdparm_sda.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sda.txt")
root@ubuntu:~# hdparm -t /dev/sda >> [/hdparm_sda.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sda.txt")
root@ubuntu:~# hdparm -I /dev/sdb > [/hdparm_sdb.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sdb.txt")
root@ubuntu:~# hdparm -t /dev/sdb >> [/hdparm_sdb.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sdb.txt")
root@ubuntu:~# hdparm -t /dev/sdb >> [/hdparm_sdb.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sdb.txt")
root@ubuntu:~# hdparm -t /dev/sdb >> [/hdparm_sdb.txt]("https://dl.dropboxusercontent.com/u/11915528/ssd-woes/hdparm_sdb.txt")

**SSD partition alignment check**
root@ubuntu:~# fdisk -l

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd162fc6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   483332095   241665024   83  Linux
/dev/sda2       483332096   500117503     8392704    5  Extended
/dev/sda5       483334144   500117503     8391680   82  Linux swap / Solaris

Disk /dev/sdb: 480.1 GB, 480103981056 bytes
255 heads, 63 sectors/track, 58369 cylinders, total 937703088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   937703087   468850520   83  Linux
root@ubuntu:~# parted 
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) select /dev/sda
Using /dev/sda
(parted) align-check opt 1                                                
1 aligned
(parted) select /dev/sdb
Using /dev/sdb
(parted) align-check opt 1                                                
1 aligned
(parted) quit                                                             

Scheduler:
root@ubuntu:~# cat /sys/block/sd{a,b}/queue/scheduler
noop [deadline] cfq 
noop [deadline] cfq 

**Mount options:**
root@fk20563:~# mount | grep sda
/dev/sda1 on / type ext4 (rw,noatime,nodiratime,errors=remount-ro,discard)
root@fk20563:~# mount | grep sdb
/dev/sdb1 on /media/vmware type xfs (rw,noatime,nodiratime,logbsize=256k,discard)

**FS read/write check of /dev/sda1 on Ubuntu**
root@fk20563:~# dd if=/dev/zero of=/test.raw bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 229.091 s, 4.6 MB/s
root@fk20563:~# dd of=/dev/null if=/test.raw
2048000+0 records in
2048000+0 records out
1048576000 bytes (1.0 GB) copied, 2.58461 s, 406 MB/s

**FS read/write check of /dev/sdb1 on Ubuntu**
root@fk20563:~# dd if=/dev/zero of=/media/vmware/test.raw bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 229.395 s, 4.6 MB/s
root@fk20563:~# dd of=/dev/null if=/media/vmware/test.raw
2048000+0 records in
2048000+0 records out
1048576000 bytes (1.0 GB) copied, 2.75578 s, 381 MB/s

**Read/write speed using SysResCd:**
root@sysresccd /root % dd if=/dev/zero of=/mnt/backup/test.raw bs=1M
count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 1.8919 s, 554 MB/s
root@sysresccd /root % dd of=/dev/null if=/mnt/backup/test.raw                 
2048000+0 records in
2048000+0 records out
1048576000 bytes (1.0 GB) copied, 2.14372 s, 489 MB/s
root@sysresccd /root % dd if=/dev/zero of=/mnt/custom/test.raw bs=1M
count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 3.93656 s, 266 MB/s
root@sysresccd /root % dd of=/dev/null if=/mnt/custom/test.raw
2048000+0 records in
2048000+0 records out
1048576000 bytes (1.0 GB) copied, 1.91224 s, 548 MB/s
root@sysresccd /root %

---

### Post by oldfred on 2014-06-20
My SSD is an inexpensive Microcenter house brand from 2 years ago.

Before when I tested with hdparm it was 208.20 MB/sec.
Just reran it in my 12.04 install in sdd3 and got 175.96 MB/sec
 and in 14.04 in sdd4 and got 177.70 MB/sec.

So a bit slower than it used to be.
I also ran your dd commands and got this:

```
fred@trusty-DT:~$ sudo dd if=/dev/zero of=/test.raw bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 3.36503 s, 312 MB/s

fred@trusty-DT:~$ sudo dd of=/dev/null if=/test.raw
2048000+0 records in
2048000+0 records out
1048576000 bytes (1.0 GB) copied, 4.42145 s, 237 MB/s

```

I am still configuring my 14.04 and may not fully convert until first point release. 

Not sure about your vmware & xfs file system. Do those support trim?
Do you have AHCI on in BIOS?

---

### Post by atterdag on 2014-06-20
Yeah, both ext4 (sda1) and xfs (sdb1) supports TRIM through the discard option, and I'm using AHCI. Also I'm using fstrim regularly.

Which chipset do you use?

---

### Post by oldfred on 2014-06-20
My system is part 2006 mostly updated in 2009.
I have EP43-UD3L vendor: Gigabyte Technology Co., Ltd. as my motherboard. (2009)
and Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz as my CPU. (2006)

So not very current, I am planning to build new system soon, but I said that when I bought SSD thinking I would move SSD to new system. But SSD improved performance enough for what I do that it became hard to justify. But now I still plan to upgrade, even though current system runs reasonably well.

---

### Post by atterdag on 2014-06-20
It breaks my heart but I start to think that I have to switch to RHEL ... urgh!

---

### Post by atterdag on 2014-06-21
hmm ... this is annoying. I don't have this problem with the 64-bit version. But I need to run some propriety software that is only supported on 32-bit.

---

### Post by oldfred on 2014-06-21
You could dual boot or install the 32bit into a VM so you also have it running? Never used a VM but many recommend it if you have the RAM & system for it.

I thought just about all 32 bit ran now in the 64 bit as they changed things to make it work.

---

### Post by atterdag on 2014-06-22
OK problem is due to that I have 32GB RAM, if I apply "mem=8GB" to the kernel options, then write speed is returned to normal. But that's not really a solution, just the reason.

---

### Post by atterdag on 2014-06-22
I've added proposed updates, and updated to kernel 3.13.0-30.54, but alas it didn't help.

---

### Post by atterdag on 2014-06-22
> **oldfred said:**
> You could dual boot or install the 32bit into a VM so you also have it running? Never used a VM but many recommend it if you have the RAM & system for it.

I thought just about all 32 bit ran now in the 64 bit as they changed things to make it work.

Its everything from my VPN, and mail client to the proprietary software from my company that only available in i386 debs. So I would need to run 64-bit Ubuntu, just to host a virtual 32-bit Ubuntu that I would work in permanently. This is of course waste of resources I will be better of choosing another OS.

In your experience would it help to create a bug report at launchpad regarding this?

---

### Post by oldfred on 2014-06-22
It cannot hurt to file a bug report, as perhaps the developers know about it and do have a fix or need to know about it.

 Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Perhaps when you get more than 8GB of RAM it does not correctly swap the RAM in and out? But if a kernel issue, it may not be a priority.

---

### Post by atterdag on 2014-06-23
Well I've made a bug report, so lets see what they say.

Trust me ... if I could run 64-bit then I would!

---

