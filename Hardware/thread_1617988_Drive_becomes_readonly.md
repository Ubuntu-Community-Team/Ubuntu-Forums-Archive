---
title: "Drive becomes readonly"
date: 2010-11-10
forum: Hardware
---

### Post by Arcath on 2010-11-10
I have /dev/sdd1 mounted to /samba/media2 it is shared through samba and has been working fine for ages but a couple of weeks ago it started complaining saying that the File system was read only, even though the server hadn't been rebooted or had anything mount related done to it. I rebooted it the first time, and the second time but its now happening more often and I'd like a solution that doesn't require me to reboot my primary server every few days. So I thought I will just umount it then mount it again only when I try to umount this happens:

```
[07:31:20][arcath@londinium][samba] sudo umount /samba/media2/
umount: /samba/media2: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

I assume this is because samba and the other media related programs that are running are looking at the drive so stopping a umount

So I tried -f, didn't work. -l did seem to but as soon as I tried to mount it again I got:

```
[07:32:31][arcath@londinium][samba] sudo mount /dev/disk/by-uuid/7048c328-3747-4b2f-9b3c-d2fb0d1303c7 /samba/media2
mount: /dev/sdd1 already mounted or /samba/media2 busy
```

obviously I cant fsck the disk whilst its mounted, and I can't umount the disk whilst its on

As a last resort I could always comment it out of /etc/fstab and try from there but I would rather have a way of doing it that didn't require me to alter my config.

---

