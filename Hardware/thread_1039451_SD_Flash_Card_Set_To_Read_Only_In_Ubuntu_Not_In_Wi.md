---
title: "SD Flash Card Set To Read Only In Ubuntu Not In Windows XP"
date: 2009-01-14
forum: Hardware
---

### Post by chiques on 2009-01-14
I have a Flash SD card with a USB adapter. When I use it in Ubuntu, it is set to "read only" and I can't change anything on the drive. When I load it in Windows XP I am able to change things on the drive. What's going on?

---

### Post by Coreigh on 2009-01-14
Does the disk auto mount when you insert it? Or do you have to execute some mount command? Where is it mounted as, what folder?

---

### Post by chiques on 2009-01-14
Hi Coreigh,
The disk auto mounts on the desktop. It mounts a SD icon which I can double click into and see the contents of the folder. There is no terminal command executed.

---

### Post by Kevbert on 2009-01-14
With the SD mounted and showing on the desktop, try entering
```
mount
```
in terminal - this will give you the device name and properties. Then enter
```
sudo mount -o remount,rw /dev/sdc1
```
where /dev/sdc1 is actually your SD device and rw is read and write access.

---

### Post by chiques on 2009-01-14
Yuck... terminal entries.


Any speculation on what caused this to change? I've been using Ubuntu for a while now with this drive and have always been able to write to it (using the GUI). This is the first time I've seen this behavior.

---

### Post by chiques on 2009-01-15
I didn't solve the problem but I have a work around. I simply used gparted and formatted the SD card with ntfs (so I can use it in my Windows part). I backed everything up, formatted and copied back. Everything is fine now.

Thanks everyone!

---

