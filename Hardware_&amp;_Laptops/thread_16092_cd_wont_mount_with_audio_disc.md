---
title: "cd wont mount with audio disc"
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by drasko on 2005-02-19
Although in fstab is set 
/dev/ide/host0/bus1/target0/lun0/cd /media/cdrw             auto    noauto,user,exec,ro 0 0
/dev/ide/host0/bus0/target1/lun0/cd /media/dvdrom           auto    noauto,user,exec,ro 0 0

for cdrw and dvd they wont mount when I insert audio disk, saying: device i/o error: can't read superblock.

Disc with mp3 music mounts without problem...

Drasko

---

### Post by grj on 2005-02-19
You cannot mount audio CDs since they do not have file systems.

---

### Post by drasko on 2005-02-20
Yes... Found out that a few minutes after a post... What a supid question I asked...
Thanks,
Drasko

---

