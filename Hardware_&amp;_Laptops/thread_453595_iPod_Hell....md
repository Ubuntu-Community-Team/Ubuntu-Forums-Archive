---
title: "iPod Hell..."
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by dbrjay on 2007-05-24
Hello all ! As the title says im having a fair bit of trouble doing anything with my ipod in ubuntu. 
I have installed gtkpod and set the options to automatically mount but nothing happens, i cannot access my pod. 
By attempting to manually mount my pod i get the following error message::

> mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount

Any suggestions would be greatly appreciated  :D

---

### Post by oddin85 on 2007-05-25
my iPod shows up as sdb2...
maybe u need to try /dev/sda2 because i think sda1 has the ipod's firmware :-)

i tried:
```
sudo mount /dev/sdb2 /mnt/ipod
```

and it mounted without issues :-)
(assuming you already have the folder /mnt/ipod)

---

### Post by dbrjay on 2007-05-25
i have tried mounting sda, sda1 and sda2. All with no luck. 
I have a folder to mount to but no luck mounting it....

can anyone advise some software which ipods use??? are there any system updates to get an ipod to run??

---

