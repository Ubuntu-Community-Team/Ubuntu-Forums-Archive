---
title: "Mounting NDAS network disk at startup"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by daldinit on 2007-04-08
I'm trying to mount an NDAS disk (a network disk called netdisk) at startup.

The rule i have added in fstab (i'm mounting the second fat32 partition):
```

/dev/ndas-08010315:0p2  /media/myhd  vfat   auto,ro    0       0

```

When doing "mount -a" once i'm in X, it actually does mount the disk, but of course i don't want to do this every boot.

My guess is that it tries to mount during boot, but when this happens either the network interfaces aren't loaded yet, or the NDAS service is not loaded yet. (i think)
So one solution would be that the "mount -a" or a similar command is issued automatically in some way, but since I'm new to Linux I don't know how to do that. Any suggestions?

Probably (?) relevant dmesg output:

```

[17179625.620000] ndas: registering network interface eth0
[17179625.620000] ndas: registering network interface sit0
[17179625.620000] ndas: fail to register network interface sit0 (-12): ignored
[17179625.656000] ndas: cache memory size 1552
[17179625.660000] ndas: registered ndas device at major number 60
[17179625.752000] ndas: discovered 1 unit device from "netdisk1"
[17179625.768000] ndas: registered device "netdisk1" is online
[17179625.796000]  ndas-08010315:0: p1 p2
[17179625.816000] ndas: /dev/ndas-08010315:0 enabled with 64 kbytes max trasfer unit

```

-And yet another thing, as you have noticed I'm using FAT32. This is because when the disk is formatted in NTFS it claims that i do not have permissions to read the content of the disk (but i -can- mount it) Any ideas why this is happening? Do I have to specify some other parameter for "mount"? A SID maybe?

Thank you!

---

