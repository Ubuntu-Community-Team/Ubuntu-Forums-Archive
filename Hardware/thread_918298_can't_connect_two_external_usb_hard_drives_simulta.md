---
title: "can't connect two external usb hard drives simultaneously"
date: 2008-09-12
forum: Hardware
---

### Post by yani1shu on 2008-09-12
I'm having this problem where if i have one hard drive connect via usb to my machine (working) and then try to connect a second hard drive via usb, the first drive disappears and only the second hard drive is left. Before i attach the second hard, hard drive is mounted listed as /dev/sdc1, when i attach the second hard drive, it assumes /dev/sdc1 and the first doesn't show up as anything. Here are the results of fdisk after attaching the second hard drive.

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16561655

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe206899

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001    7  HPFS/NTFS


Shouldn't one of the external drives be sdb and the other one sdc?

Thanks for any assistance you can give

---

### Post by Thanoulis on 2008-09-12
I assume that you've got a CD-ROM, so this is your sdb. The normal is to have first usb-drive as sdc and second as sdd. The auto-mount thing is *fuse*. So try to check out your *fuse* settings.

---

### Post by yani1shu on 2008-09-12
where do i find my fuse settings and what should i be looking for?

Thanks  for replying

---

### Post by IntuitiveNipple on 2008-09-13
Reproduce the issue again and then please attach a (compressed) copy of /var/log/kern.log so we can examine what is happening:
```

cat /var/log/kern.log | gzip > kern.log.gz

```

---

### Post by yani1shu on 2008-09-13
Here it is.
FYI: The 500Gb hdd the drive attached original, was set to sdb1, the second drive attached is set  to sdc1, so it's not like they're conflicting, but sdb1 still disappears.

---

### Post by yani1shu on 2008-09-16
Any one have any ideas/suggestions?

---

