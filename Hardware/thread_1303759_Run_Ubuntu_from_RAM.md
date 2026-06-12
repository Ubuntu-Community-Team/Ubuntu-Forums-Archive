---
title: "Run Ubuntu from RAM"
date: 2009-10-28
forum: Hardware
---

### Post by Faun on 2009-10-28
Hi,

I'm currently building a PC which will be used mainly as a NAS/Media Server running 24/7 and I don't want Ubuntu to prevent my hard drive from spinning down when it's not used.

Would this be possible:
Install Ubuntu onto a software raid1 consisting of 1 hard drive partition.
After booting add a ramdisk to that raid, wait until the data is replicated and remove the partition.
Before shutting down the data could be replicated back to hdd in the same way.

And is it possible to boot after a power failure, since the hard drive wouldn't be part of the raid at that time. Could I add the hdd to the raid using a live cd?

Thanks in advance.

---

### Post by Giblet5 on 2009-10-28
That would be difficult to implement and debug.

What I did:

Old HP Omnibook laptop with a 1.3Ghz Pentium III, 512MB RAM, and a 40GB disk drive.

I installed Ubuntu server edition, nfs, mediatomb, MySQL, Apache2, postfix, dovecot, and bind9.

Then I plugged in my RAID1 USB drive and exported it via NFS and Samba shares. I configured mediatomb to work with my PS3.

The laptop's hard drive I made sleep after 10 idle minutes via ```
hdparm -S120 /dev/sda
```

The RAID1 drive goes to sleep after 30 seconds ```
hdparm -S6 /dev/sde
```

That puny laptop serves Web service, Samba, NFS, DNS, email, media and a Movie database (phpdvdcollector) and it uses very little power. It runs cool, doesn't wear itself out, and my DNS lookups scream (microseconds instead of milliseconds/seconds).

So, I recommend the weak/wimpy/low-power cpu unit (laptop in my case) and the external RAID1 for media storage.

That's been the architecture at my house since Dapper was released, w/o any downtime, so you decide if it's reliable or not. ;)

---

