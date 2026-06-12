---
title: "Toshiba A60, FAT32 partition problem - Kubuntu"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by alquimista on 2005-07-21
Hi,
I have just installed Kubuntu 5.0.4 on a Toshiba Satellite A60; I'm new to Linux world and I setup my HD to have 3 partitions: 
1- NTFS (about 30 Gb)
2- FAT32 (to share data for Win and Linux, about 20 Gb)
/dev/hda5           75571      116280    20517808+   b  W95 FAT32

3- Linux (10 Gb)

I wanted FAT32 partition to have read/write permissions for any user; so, following a text I found on generla Linux, the recomendation was to write in fstab something like:

/dev/hda5	/media/datos	vfat	user,rw,exec,nosuid,noauto,gid=100   0 0

It did work just for read; I could not write.

Then, in the "unofficial ubuntu 5.0.4 Starter Guide" they suggested:
/dev/hda5       /media/datos    vfat    iocharset=uft8,umask=000        0      0

Didn't work either.

I'd appreciate eny help please.

Thank you,
Guillermo

---

