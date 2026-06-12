---
title: "Automounting External HDD's and Multiple Partitions"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by zheepeez on 2007-06-13
I've got an XP/Ubuntu dual boot and I'm running the following in terms of discs:

[LIST]
[*]External HD, NTFS
[*]Internal ext3 boot partition (linux)
[*]internal ntfs boot partition (Windows)
[*]internal partition ext3, non-boot, for media
[*]an iPod
[/LIST]

I've got the ext3 extension for Windows and ntfs-3g on Ubuntu (Feisty). The external HD (ntfs) won't mount cleanly because "this disc is scheduled for a check".  It recommends booting twice into windows (which didn't work) and suggested I mount it manually, which I've been doing with the code:

```
sudo mount -t ntfs-3g /dev/sda1 /media/External -o force
```

which works, but I'd like it to happen manually (me /= code monkey).

Also, the ext3 internal drive doesn't auto-mount, and when it does it mounts to /media/disk (or /media/disk1 if the NTFS partition's mounted) rather than the named mountpoint i mkdir'd and mounted it to using the code above. I've heard brief mention of /etc/fstab but I don't want to change it until I understand it fully, so could someone please explain **where can I configure auto-mount points for internal and external drives?**

Thanks

---

