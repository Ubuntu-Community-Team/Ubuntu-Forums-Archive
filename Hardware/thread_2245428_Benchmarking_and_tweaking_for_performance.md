---
title: "Benchmarking and tweaking for performance"
date: 2014-09-23
forum: Hardware
---

### Post by Michael_McKenney on 2014-09-23
I know the performance on this workstation when it was Windows XP Pro x64.  How do I check the performance of Ubuntu 14.04 on this workstation.  I want to make sure the video adapter and NIC are getting similar benchmarks.  Any notes on tweaking the Gbps NIC settings to increase performance?

---

### Post by TheFu on 2014-09-23
There are tools for monitoring network bandwidth, disk I/O and other system performance characteristics.  For desktop users, Conky is the usual tool. [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)  For administrators, the systats package and data capture tools over that are commonly used - something like cacti or sysusage or ... there must be 20 of them. Generally, the setup for them is 100x harder.

Standard Unity desktop Ubuntu has performance manager. Did that no do what you want? It is like the Windows Perf Mon.

Tuning network cards will be driver and network specific.  Things like ethtool and iperf [http://manpages.ubuntu.com/manpages/trusty/man1/iperf.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/iperf.1.html) will help.  Settings that are good for desktops aren't so good for servers and vice versa. Servers need to support lots of different transfers concurrently and remain responsive. On a desktop, we want to push the data as fast as possible and are willing for responsiveness to drop, more.

Disk I/O - hdparm. Be careful. There is a complete stack of hardware, drivers, settings, tools, options here.  They all need to be understood and work together.  It is easy to make performance worse, especially with RAID setups. [http://www.jamescoyle.net/how-to/599-benchmark-disk-io-with-dd-and-bonnie](http://www.jamescoyle.net/how-to/599-benchmark-disk-io-with-dd-and-bonnie)

So ... what do all these tools do for most desktop users?  Not too much.  They are really more for server admins to get that last 20% with trade-offs in general compatibility.

In the end, good-enough is the performance we all need. Trying to tune a 10/100 network really isn't worth the time; same for wifi networks. Don't bother.  Just get 1000base-tx equipment (NICs, switches/routers and CAT5e cables), get 650-800 Mbps network throughput and be happy. This is more than most HDDs can support, so moving files around on a GigE network becomes a disk subsystem optimization issue.  Generally, fast spinning disks only write around 125Mbps, so if you don't read and write to SSDs, faster doesn't matter.  With a good RAID card, it is possible to get 300Mbps on disks. I don't have that card and my RAID setups are lucky to get 40Mbps. The OS handles the disk buffering automatically.

Hope this all helps.

---

### Post by Michael_McKenney on 2014-09-23
the hardware is server grade.  However, I am the only user other than the backup drives and Bacula.  I don't overclock anything.  I usually start ramping up NIC settings 10% at a time.  All three workstations have Gigabit.  The Tyan board has server NIC onboard.  All the cables are CAT 6.  I am not worried about hard drive performance.  The SATA drives on the two Ubuntu boxes run at decent speeds.  SATA drive average 80 MB/s.  Windows 7 has data center SAS RAID and 15K SAS drives.  1.097 GB/s cached reads and 850 MB/s cached writes.  If you want SATA RAID to be fast.  Don't do RAID 5 only RAID 10.

I am looking for NIC and video adapter performance.  I will look at your recommendations tonight.

---

