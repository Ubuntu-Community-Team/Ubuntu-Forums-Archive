---
title: "USB ext3 + macbook = no good"
date: 2009-02-16
forum: Hardware
---

### Post by reev3r on 2009-02-16
I recently got a macbook and plugged my 500Gb USB disk into it. The disk was formatted ext3 which os x does not recognize. However, I did get it working in OS X by removing journaling in Ubuntu, sadly it was read-only. So I went back into Ubuntu to modify the disk, but ended up destroying the partition structure. I was ultimately able to recover my data although now it shows up in gparted as unallocated, but I am fully capable of browsing the disk in Nautilus. Needless to say, the disk s not accessible in OS X. I have tried many options for recovery though none of them seem to be helping.

Again, the data is all there, and is fully browsable.

Sadly I have to VNC into the Ubuntu machine to make any modifications, since it is a server at my girlfriends house.

Regardless, included is a screenshot of what I see in gparted.

If you could help me sort this out I would be eternally grateful.

Why ext3 is not supported by OS X is a mystery to me.

Thanks,

reev3r

---

### Post by jespdj on 2009-02-16
So, you can see the data with Nautilus, but GParted shows you that something's wrong with the partition structure? I'd copy the contents off of the disk, then repartition it, and copy the data back.

> **reev3r said:**
> Why ext3 is not supported by OS X is a mystery to me.
Why would you expect OS X to support ext3? OS X is not Linux (and it's not even based on Linux, despite what some people think). Windows also doesn't support ext3.

---

### Post by reev3r on 2009-02-16
I have been thinking that I may be forced to copy the data elsewhere, sadly, it being a 500Gb drive, I no longer have several hundred gigs of storage laying around as I used to, having traded my Windows gaming rig for a macbook.

With regards to OS X not being Linux, I am aware it is not Linux, however, it is Unix based, as well as using an implementation of X11.

"Mac OS X is based on the Mach kernel and is derived from the Berkeley Software Distribution (BSD).[7] Certain parts from FreeBSD's and NetBSD's implementation of Unix were incorporated in Nextstep, the core of Mac OS X."

So Linux, no, Unix, yes.

Not trying to start a flamewar or anything. OS X mounted the ext2 file system fine for me, so you would think that with the only difference being journaling it would have been implemented. Just my thoughts anyhow.

Thanks for the help, I am taking your advice since it is likely the safest course of action, I have most of the data backed up on two servers, one at my girlfriends, one at home, so I will only need to copy about 30Gb of data.

Thanks again,

Jacob

---

### Post by reev3r on 2009-02-16
p.s.

Windows sucks with anything not windows, in fact, even in starting a computer with a drive of any format windows writes data to the disk, and in some cases corrupting the file system.

---

