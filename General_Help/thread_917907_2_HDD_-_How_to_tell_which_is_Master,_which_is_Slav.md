---
title: "2 HDD - How to tell which is Master, which is Slave?"
date: 2008-09-12
forum: General Help
---

### Post by SSVegito888 on 2008-09-12
I have 2 identical HDD on my notebook pc.

I was wondering which is registered as Master and which is registered as Slave.

Is there a way to find this out without opening the notebook case.


PS: I am using Ubuntu 8.04 Hardy.
    

PPS: Also, I am still sort of new to Linux, so please give specific         instructions.

---

### Post by ibuclaw on 2008-09-12
The Harddrive named **sda** is most commonly the Master HardDrive.
The other (**sdb**) will be the slave.

To have that information printed:
```
sudo lshw -C disk -html >~/Desktop/hardwareinfo.html
```
And check your desktop for the newly created file.

Regards
Iain

---

### Post by SSVegito888 on 2008-09-12
Thanks.


I have one more question though.

Why does ubuntu use disk, disk-1, instead of sda, sdb, etc.


Thanks Again,

SSVegito888

---

### Post by gldearman on 2008-09-12
The one wearing the gimp mask is the slave.  The one holding the whip is the master.

No, seriously ...

A simple way to determine which is which is to check your settings menu in your BIOS.

sda, sdb, etc are references to the devices.  disk, disk-1, etc. are the *mount points* of the devices.  They appear in the /media/ directory.

---

