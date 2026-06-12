---
title: "Hibernate Problems after resizing"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by thor27 on 2007-01-16
After resizing my /dev/hda2, using a live CD, I removed my old swap at the end of the disk and created a new one using all the free space

It was something like that

```
/dev/hda1 50gb [ext3]
/dev/hda2 50gb [ext3]
/dev/hda3 512mb [swap]

```
And I changed to something like that:

```
/dev/hda1 50gb [ext3]
/dev/hda2 49.5gb [ext3]
/dev/hda3 1gb [swap]

```

 but than my swap stoped mounting, so I changed in /etc/fstab:

```
# /dev/hda3
UUID=be960b81-4131-42ab-a098-c41152b22771 none            swap    sw              0       0
/
```

to:

```
# /dev/hda3
UUID=60e5cfed-b822-491f-bb7a-c448cf9ea05a none            swap    sw              0       0
/
```

as I saw in a ls -la /dev/disk/by-uuid/

so I rebooted and swap started working as I saw in free -m.

but then hibernate stoped working, and I saw in dmesg
```
[  156.656000] swsusp: Cannot find swap device, try swapon -a.
```


What I have to do to swsusp detect my swap?


I'm using Kubuntu 6.10 with 2.6.20-2-generic kernel (from 7.04)

Thanks!

---

### Post by thor27 on 2007-01-17
Updating the kernel to 2.6.20-5 fixed this issue.

---

