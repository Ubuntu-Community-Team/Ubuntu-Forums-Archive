---
title: "can't see WD external drive?"
date: 2011-02-10
forum: Hardware
---

### Post by knurledflanges on 2011-02-10
I have a 1tb WD Elements USB external hard drive with a single FAT32 partition and Ubuntu 10.4 w/ full updates. The drive and my bios/mobo have never  played nice together -they've never posted with the drive plugged  in- but everything about the drive worked perfectly in Ubuntu 9.10 and Windows before it, and any Windows machine or Mac I try it with now. lsusb sees it on the Ubuntu machine. It doesn't show up in df. I'm not really technical and have no idea how to approach this. This machine is almost 100% very old hardware and sort of on it's last legs, plus takes some fiddling every time I do OS stuff to it, so I'd really rather not mess around with updating the OS to have it maybe or maybe not work. Thanks!

---

### Post by walle1357 on 2011-02-10
Please run the following command and post the output here.
sudo ls /dev | grep sd

---

### Post by knurledflanges on 2011-02-10
Hi there, and thanks for the reply. With the drive plugged in I get:
```
sda
sda1
sdb
sdb1
sdb2
sdb5
```

---

### Post by knurledflanges on 2011-02-16
Follow up: in addition to working fine on other machines, the drive seems to work fine on this machine when testing other linuxes off of livecd (I've only tried it with Puppy though).

---

