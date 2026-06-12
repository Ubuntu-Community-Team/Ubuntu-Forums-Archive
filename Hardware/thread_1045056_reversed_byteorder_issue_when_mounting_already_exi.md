---
title: "reversed byteorder issue when mounting already existing raid 5"
date: 2009-01-20
forum: Hardware
---

### Post by Langsdorf on 2009-01-20
hello raid specialists,

we have a problem with assembling a RAID5 (4 hdd) from our NAS, which doesn't work anymore. We are pretty sure the byteorder is reversed. We put the hdds in an old computer and booted the hardy heron live cd and installed mdadm to get the raid working again.


```
mdadm --examine --metadata=0.swap /dev/sd*3
```

gives the correct information about which partions/hdds are in the raid and

```
mdadm -Cv /dev/md0 --update=byteorder --level=5 --raid-devices=4 /dev/sd[abcd]3
```

says the option update to reverse the byteorder is not allowed. When we skip this option everything works fine until we want to mount the device

```
mount -t xfs -o norecovery,ro /dev/md0 /mnt/...
```

then it says bad superblock/wrong filesystem, which is obvious, because the byteorder is reversed. The steps in between are

```
mdadm --detail --scan > /etc/mdadm/mdadm.conf
```

(a friend said that this should take a long time, but we get the uuid after some seconds, we are not sure it is working correct)

```
mdadm -S /dev/md0
```

to stop the raid and

```
mdadm -As /dev/md0
```
to assemble it.

Do you have any idea how it can be done? It appears to us that its working, despite the byteorder

---

