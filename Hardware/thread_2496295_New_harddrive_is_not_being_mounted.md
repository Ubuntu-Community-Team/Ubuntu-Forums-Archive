---
title: "New harddrive is not being mounted"
date: 2024-03-22
forum: Hardware
---

### Post by claus on 2024-03-22
Hi all,

I have a new harddrive inside my PC. The only problem ist that it is not being automatically mounted. I added the following line to /etc/fstab
```
/dev/sdb1 on /home/claus/neue_Platte type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```
but for some reason this is not working. How can I solve this problem? Mounting the drive manually works.

TIA,

Claus

---

### Post by Holger_Gehrke on 2024-03-22
That line should read
```

/dev/sdb1 /home/claus/neue_Platte vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 2

```
No 'on', no 'type', no parentheses around the option. For details look at 'man 5 fstab'. Personally I wouldn't use a device name, those aren't guaranteed to stay the same from one boot to the next. I'd use either 'GUID=...' or 'LABEL=...'.

Holger

---

### Post by claus on 2024-03-22
Thanks, it works now.

Claus

P. S.: Where do I find the GUID?

---

### Post by oldfred on 2024-03-22
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
The partuuid is the unique guid.

There also are partition type guids.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

Good examples:
[https://wiki.archlinux.org/index.php/fstab](https://wiki.archlinux.org/index.php/fstab)
I mostly use UUIDs, but like labels or partlabels.

---

