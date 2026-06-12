---
title: "MB raid0, raid5 incorrect size"
date: 2014-05-27
forum: Hardware
---

### Post by mm7hKDW on 2014-05-27
Hello, i could appreciate some help with ubuntu raid.

I have 6 x 3tb disks, and i want to create a raid5 with them.

I have intel H87 chipset motherboard, so i did the setup in the raid configuration which was successful.

Ubuntu detects the raid volume, i can format it, mount and write, but the size is incorrect(in gparted too). It shows that the raid5 volume is only 4TB. Is it a bug, or i'm missing something?

Thank you.

---

### Post by mm7hKDW on 2014-05-28
It seems, that dmraid is unable to correctly detect the raid5 volume. However mdadm can. But somehow, it only does if i manually scan the volume after every boot. In disks the volumes appear as /dev/md127 etc, but mdadm --detect --scan gives other values so the mdadm.conf is not correct.

---

### Post by mm7hKDW on 2014-05-29
Really strange, maybe a bug, everything is correct now. I created mdadm.conf, and its perfectly working. i did upate-initramfs, but mdadm not assembling raid at boot. Any suggestions?

---

### Post by mm7hKDW on 2014-05-29
I downloaded mdadm 3.3 debian package and installed it. It is working as it should. Something was wrong with the ubuntu package the whole time.

---

