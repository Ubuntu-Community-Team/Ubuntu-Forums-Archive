---
title: "Reasonable partition sizes"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by sbw87 on 2009-11-07
Hi,
I have just purchased a new server system with a 500 GB hard drive in it (doubled by hardware RAID). I am not completely new to Ubuntu, but have never worked with the **server edition**. Could anyone please give me a hint on how to reasonably partition my HDD using LVM? Apart from ordinary server tasks, I need a basic GUI (e. g. fluxbox) for some special WINE tasks (I have a weather station depending on proprietary windows software).

Other tasks to be fulfilled by the server:
- file server
- DNS
- Apache/PHP webserver, probably needing around 30 GB of webspace
- OpenSSH
- VPN

Thanks a lot,
sbw87

---

### Post by SaintDanBert on 2009-11-07
Partitions and sizes are somewhat of a "religious" issue. There are almost as many unique answers to this question as there are folks who ask it. I suggest that you take some time to understand drives and partitions in general. I find this article [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning) a good place to start. It is generic, but covers the basics.

For a server, I strongly encourage you to use at least two physical drives: (1) for the distro and programs, etc, and (2) one for end-user data. It will make a significant difference in your server performance. Remember, something will as the "programs disk" to find and read-in a program and its parts. The program will then ask the "data disk" to find and read-write some data. If you have a busy server, two drives lets these operations to overlap.

Here is what I have done on past servers:
[list]
[*]**primary #1 -- ** /boot ...
[*]**primary #2 -- ** swap ... at least as large as system RAM
[*]**primary #3 -- ** / ... 
[*]**primary #4 -- ** Extended partition
[list]
[*]**logical #5 -- ** /var ... run-time and other transient files
[*]**logical #5 -- ** /opt ... installed application parts
[*]**logical #5 -- ** /home ... all of your per-user files
[*]**logical #5 -- ** /wrk ... the rest of the drive
[/list]
[/list]

The sizes depend on your situation and the purpose of your server.
With a second drive, I put another swap partition and one or two other data partitions. I then mount these data file systems under /wrk on the "system disk".

I hope this gets you started,
~~~ 0;-Dan

---

### Post by sbw87 on 2009-11-07
Hi,
thanks for your answer. I've already set up and worked with quite a lot of (productive) desktop systems, so I'm fairly familiar with partitioning basics. What's more, given the case of a full hardware-RAID-1 mirroring, I'll probably have the same advantages (reading in parallel) as with two separate drives, won't I? (Of course, I have some non-RAID backup disks for the unlikely but possible event of a controller failure.)

The thing I have nearly no experience with is the typical reasonable-seeming size of root, /boot, /var, /usr and /opt partitions in a server environment. I suspect my experience with desktop systems all having a considerable amount of software installed doesn't help me that much with a server OS, right?

Thanks
sbw87

---

