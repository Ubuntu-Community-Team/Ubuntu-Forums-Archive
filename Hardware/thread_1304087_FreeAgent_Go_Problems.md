---
title: "FreeAgent Go Problems"
date: 2009-10-28
forum: Hardware
---

### Post by psphacker22 on 2009-10-28
Hello, im having some trouble with my 320GB FreeAgent Go External HDD. it mounts and works perfectly when my computer boots and continues to do so for about 10 mins. after.
than it sudddenly dissapears. i usually try unplugging it and plugging it back in and that doesnt work. the computer doesnt even aknowledge that it is plugged in. it is formatted NTFS and works fien on both of my windows computers. any help would be appreciated, thanks

---

### Post by Aemaeth on 2009-10-29
you could always try a sudo mount

find your device using
ls /dev
and look for something like /sdb1 or sdc1
then try to mount it to a directory 
create the directory
sudo mkdir /media/freeagent
then mount it
sudo mount -t ntfs-3g /dev/sdc1 /media/freeagent

good luck

---

### Post by psphacker22 on 2009-10-29
well, that didnt work, anything else?

---

### Post by psphacker22 on 2009-11-04
been a few days, anyone have any other possible solutions?

---

