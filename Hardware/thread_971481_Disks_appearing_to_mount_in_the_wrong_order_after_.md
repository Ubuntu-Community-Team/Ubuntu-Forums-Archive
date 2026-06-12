---
title: "Disks appearing to mount in the wrong order after upgrade"
date: 2008-11-05
forum: Hardware
---

### Post by potatan on 2008-11-05
Hi,

I recently upgraded from Hardy to Intrepid and now my disks appear to be mounting incorrectly. Note, this doesn't happen at every boot, it only affects me about 3 times out of 5 which seems odd.

I have four drives attached - one for the system, one for my data, which is accessed via symbolic links from my /home folder, one for backups, and one for Windows.

Following a successful boot, gparted tells me this:
```

Disk     FS         Mountpoint       Label   
sda
 sda1    ext3       /
 sda2    extended
 sda5    linux-swap

sdb
 sdb1    ext3       /media/sdb1      data

sdc
 sdc1    ntfs       /media/sdc1

sdd
 sdd1    ext3       /media/sdd1      backups
```

Following an *unsuccessful* boot:

```

sda
 sda1    ntfs

sdb
 sdb1    ext3        /, /media/sdb1
 sdb2    extended    
 sdb5    linux-swap

sdc
 sdc1    ext3        /media/sdc1     data

sdd
 sdd1    ext3        /media/sdd1     backups
```

So sdc somehow becomes sda, sda becomes sdb, sdb becomes sdc, etc.

Also note that my data drive appears to be mounted twice, at / and at /media/sdb1.

I can still access the drives via the "Places" menu, but they appear under "Removable Media". Also, my symbolic links to "Documents", "Music" etc. are now broken, because they point to the wrong place.

It is baffling me as to how these things seem to move around in an unpredictable fashion following a reboot. So two questions, I guess:

1. Why is this happening since upgrading to 8.10?
2. Once the system has booted "correctly" (i.e. all drives where they should be), is it possible to do something to make that state permanent?

Many thanks in advance.

Paul

---

### Post by MeanEYE on 2008-11-05
Hm, I had the same thing about **removable media**... Never really paid attention to it since everything worked like it should.

Tell me, what are your settings for SATA controler in BIOS? I had to put mine in compatibility mode because of stupid windows. Maybe that is the problem...

But that's just thinking aloud!

---

### Post by potatan on 2008-11-06
I'll check next time I reboot, thanks for the tip.

---

