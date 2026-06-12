---
title: "RAID: Uses only one disk for reading"
date: 2009-09-06
forum: Hardware
---

### Post by atlesn on 2009-09-06
I came across this interesting issue while watching disk performance on a server.

I have two 1/2 TB SATA disks in (fake) HW-raid RAID-1 using dmraid and SiI 3114-controller.

The system uses only one of the disks while reading, as you can see here.
```

07. sep. 2009 kl. 04.29 +0200
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0,14    0,00    0,81    1,40    0,00   97,79

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sdd               2,90         0,00         0,23          1      32195
sde               6,40         0,14         0,23      19333      32195
```Does anyone know why? How can I make the system use both?

Is not really a problem, but i reckon it would be best for the lifetime of the disks if used evenly.

Other information:

Kernel is 2.6.28-13-server
Running Ubuntu Jaunty
```

# dmraid --version
dmraid version:         1.0.0.rc15 (2008-09-17) shared 
dmraid library version: 1.0.0.rc15 (2008.09.17)
device-mapper version:  4.14.0
```Appreciate any help

---

### Post by ronparent on 2009-09-06
You have a mirrored raid. I believe the raid protocol automatically replicates any writes to the second drive in sync with the first. That being the case, as long as the raid is intact, it is not necessary to read data on both drives. They are identical. If for any reason they aren't the system would indicate raid errors whenever you tried to access them.

---

### Post by atlesn on 2009-09-07
I know the disks are equal, that's not the issue.

Is this one-disk-read-behavior indented, or should both be used for reading?

---

### Post by IcarusR on 2009-09-08
Raid 1 mirrors one drive to the other (as said above) like a backup.
As far as I am aware it only reads from one drive.
Raid 1 is not designed to increase read/write speeds.

---

### Post by rob-ward on 2009-09-08
This is actually a good thing, if you had two identical drives bought on the same day and all the reads were happening on both as well as the writes then the likelyhood of them both failing at a similar time is increased meaning the likelyhood of you loosing data is increased. By only readin from one hard drive and being consistant about which one with two identical drives the one that is being read off of all of the time should fail before the one with no reads, meaning you then go out and buy a shiney new drive and no data is lost. 

This may not sound good because you are having a drive die sooner than if the reads were evenly distributed however mirroring is about preserving data.

---

### Post by Flywest on 2009-09-25
AFAIK, it's a bug in dmraid. It's been reported in the Gentoo buglists.  I have noticed the same problem on one of our servers here. It's actually a dev server we use remotely and random disk accesses in read are painfully slow.  Whenever you start a svn update or something that will poll alot of files, the process falls into D state and everything else then slows to a crawl. Processes started after that also falls in the D state.

A raid 1 usually has better read performance than a single drive FWIW.

---

### Post by atlesn on 2009-09-25
've you got a link to the bugreport?
 
> **Flywest said:**
> AFAIK, it's a bug in dmraid. It's been reported in the Gentoo buglists. I have noticed the same problem on one of our servers here. It's actually a dev server we use remotely and random disk accesses in read are painfully slow. Whenever you start a svn update or something that will poll alot of files, the process falls into D state and everything else then slows to a crawl. Processes started after that also falls in the D state.
 
A raid 1 usually has better read performance than a single drive FWIW.

---

### Post by b68 on 2009-09-30
[http://bugs.gentoo.org/230950](http://bugs.gentoo.org/230950)

---

