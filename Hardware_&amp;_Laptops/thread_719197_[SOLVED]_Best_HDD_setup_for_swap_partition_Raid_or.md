---
title: "[SOLVED] Best HDD setup for swap partition? Raid or not?"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by MountainX on 2008-03-08
It is often recommended to put the swap partition on a separate drive. Now it is also recommended to run virtual machines on a separate drive from the OS drive.

My question is which would be better for **performance** if I have three (or 4) drives available:
1. OS on one drive, swap on another, and virtual machines on the last drive?
2. set up all drives in RAID 0 (striped) configuration using a fast RAID controller and run everything from the RAID array?

Thanks.

UPDATE:
I'm asking for opinions (hopefully informed ones) about the relative performance of multiple individual disks vs. a good striped raid configuration for specific applications where disk contention can cause a bottleneck.

My theory is that a good raid controller with a striped (raid 0 or raid 1+0, etc.) volume is the better choice even though people routinely recommend a separate disk.

I'm looking for comments about *performance.* Thanks.

---

### Post by Yellow Pasque on 2008-03-08
RAID 5 using linuxraid would be best (with 4th drive as hot spare) IMHO. If you use nvraid, you're kind of stuck with only having the system compatible with nForce south bridge/MCP's: [http://www.tomshardware.com/2007/07/10/the_raid_migration_adventure/page7.html](http://www.tomshardware.com/2007/07/10/the_raid_migration_adventure/page7.html)

RAID0 is a no-no unless you have the capability to make frequent backups.

You might want to see if your system even uses any swap before worrying too much about putting it on a separate disk. How much RAM do you have? (run free -m)
For example, here's mine while running some browser tabs, IRC, WINE/fb2k, a terminal, a nautilus window, gtk-gnutella, thunderbird. As you can see it's not using any swap cebause I have almost 2GB RAM available.
```
dan@harvest:/etc/X11$ sudo free -m
             total       used       free     shared    buffers     cached
Mem:          1888       1873         15          0         95       1065
-/+ buffers/cache:        712       1175
Swap:         5530          0       5530
```

---

### Post by MountainX on 2008-03-08
Thanks for the reply. I'm really trying to understand the true performance implications. I'm not concerned about redundancy. I will not be using RAID 5 for this application because the write speeds are slower than a single disk. If I need redundancy I'll use RAID 1 + 0, but actually I only want to know which option will give the best performance. (I'm asking as much for educational reasons as anything else.)

Also, keep in mind that I plan to run virtual machines on this server, so even if I am not using swap space at a particular time, the performance bottle neck in a virtual machine is disk access.

---

### Post by polmir on 2008-03-09
This is post about raid:
[http://www.google.pl/search?hl=pl&q=Raid+site%3Aubuntuforums.org&btnG=Szukaj+w+Google&lr=]("http://www.google.pl/search?hl=pl&q=Raid+site%3Aubuntuforums.org&btnG=Szukaj+w+Google&lr=")

---

### Post by MountainX on 2008-03-09
I think I need to clarify my question. I'm not asking about raid. I'm asking for opinions (hopefully informed ones) about the relative performance of multiple individual disks vs. a good striped raid configuration for specific applications where disk contention can cause a bottleneck.

My theory is that a good raid controller with a striped (raid 0 or raid 1+0, etc.) volume is the better choice even though people routinely recommend a separate disk.

I'm looking for comments about performance. Thanks.

---

### Post by MountainX on 2008-03-22
Solution:
It is better to have swap file on a separate disk from the OS rather than on raid on the same set of disks as the OS.

---

