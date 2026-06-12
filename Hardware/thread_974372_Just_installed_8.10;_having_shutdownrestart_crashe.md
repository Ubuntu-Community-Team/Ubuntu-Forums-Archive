---
title: "Just installed 8.10; having shutdown/restart crashes"
date: 2008-11-07
forum: Hardware
---

### Post by ioeth on 2008-11-07
**_Background:_**
I decided to do a fresh install of Intrepid Ibex instead of upgrading my Hardy Heron installation, mostly because I wanted to repartition my primary hard drive to have /home on a separate partition for easy future upgrades.  Hardy worked very well overall on my laptop, so I was really looking forward to moving to Intrepid.

**_The system:_**
HP Pavilion dv8000 laptop
AMD Turion ML-44
ATI Radeon xPress 200M graphics
Broadcom wireless

**_The problem:_**
My problem appears to be exactly the same as the problem outlined in this thread:

[http://ubuntuforums.org/showthread.php?t=918967]("http://ubuntuforums.org/showthread.php?t=918967")

I'm reinstalling Intrepid right now to make sure that it just wasn't a fluke, but I noticed that the problem is actually occurring when I shutdown/restart from running Intrepid from a live CD.  I'll post the details of what I'm seeing when I shutdown in a few minutes here.

Thanks in advance for the help!

---

### Post by phidia on 2008-11-07
The link you provided is dated 9-13-08 so that would have been prior to final relase.
You could check launchpad for bugs though.

Checking your logfiles from /var/log/messages & and other logs there may be the most productive though.

---

### Post by ioeth on 2008-11-07
**_The crash:_**

[ 1533.748012] Process usplash (pid: 875, threadinfo ffff880075990000, task ffff880074192ce0)
[ 1533.748012] Stack:  ffffe20001cc1c80 ffff880075991d88 ffff8800308717f0 000ffffffffc0000
[ 1533.748012]  ffffffffc0000000 0000000040400000 0000000000400000 ffff8800464114f0
[ 1533.748012]  ffff880075991db8 ffffffff80236d9a fffffff80a3efb22 ffff880046411468
[ 1533.748012] Call Trace:
[ 1533.748012]  [<ffffffff80236d9a>] phys_mem_access_prot_allowed+0xba/0x170
[ 1533.748012]  [<ffffffff80400707>] mmap_mem+0x87/0x150
[ 1533.748012]  [<ffffffff802c6fa9>] mmap_region+0x239/0x5d0
[ 1533.748012]  [<ffffffff802c4b49>] ? find_vma+0x9/0xb0
[ 1533.748012]  [<ffffffff802c7824>] do_mmap_pgoff+0x3f4/0x420
[ 1533.748012]  [<ffffffff8021791e>] sys_mmap+0x10e/0x140
[ 1533.748012]  [<ffffffff8021285a>] system_call_fastpath+0x15/0x1b
[ 1533.748012]
[ 1533.748012]
[ 1533.748012] Code: d0 48 8b 15 6d 7c 41 00 48 8b 4d d0 48 83 c0 18 48 89 05 5e 7c 41 00 48 c7 41 18 40 e6 64 80 48 89 51 20 48 89 02 e9 8a fd ff ff <0f> 0b eb fe 66 0f 1f 44 00 00 48 8b 4a 20 e9 49 fd ff ff 48 83
[ 1533.748012] RIP  [<ffffffff802369fe>] reserve_memtype+0x3be/0x590
[ 1533.748012]  RSP <ffff880075991d28>

---

### Post by ioeth on 2008-11-07
> **phidia said:**
> The link you provided is dated 9-13-08 so that would have been prior to final relase.
You could check launchpad for bugs though.

Checking your logfiles from /var/log/messages & and other logs there may be the most productive though.

Attached (in messages.tar.gz) is /var/log/messages after a fresh install and 1 (failed) reboot.  I'm not really sure how to interpret anything in it, so hopefully someone else might be able to help out there.

---

### Post by phidia on 2008-11-07
The message > kernel cannot find map file repeats and seems significant.
There is a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277924/+viewstatus") that looks related but no action has been taken on it.

If you want to file a seperate bug or subscribe to that one there are details on how to do that [here]("http://www.ubuntu.com/community/reportproblem").

---

### Post by ioeth on 2008-11-07
It looks like the whole problem was related to a graphics card driver issue.  After enabling the "ATI/AMD proprietary FGLRX graphics driver" for the ATI Radeon xPress 200M, the problem went away...for now, at least.

---

### Post by rofu on 2008-11-09
Im also having video problem.

How do I "enabling the "ATI/AMD proprietary FGLRX graphics driver" for the ATI Radeon xPress 200M" ?

---

