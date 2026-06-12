---
title: "Can't mount usbstick on my laptop"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by g99 on 2007-12-25
Hi!

I'd like to mount  an usbstick, but it doesnt work.I checked /etc/fstab, and it doesnt contain a row that defines the usage of the usb port. I checked the choices in /media (i dont know exactly if this is the right place) but i dont know which should i choose and with which options. 
Please give me an advice or just tell me if I'm totally wrong :)

Thx & merry Xmas !

ps: i have an asus l3800 laptop and (i think) an usb 1.1 port. But maybe it doesnt matter in this case.

---

### Post by eggdeng on 2007-12-25
Plug in the device and run
```
dmesg | tail
```
This will tell you how the device and its partitions are recognised. Unless you get an error here, try to mount it manually as follows:
Create a folder to mount the drive to 
```
sudo mkdir /media/usbdrive
```
Mount the device (assuming the device is sdb and the partition sdb1)
```
sudo mount /dev/sdb1 /media/usbdrive
```

---

### Post by vanadium on 2007-12-25
Indeed an USB should mount automatically. If it doesn't, then it probably indicates a problem with the file system. Try mounting it manually as eggdeng suggests. Error messages will give an indication of what is wrong. Post the output here for further help if needed.

---

### Post by g99 on 2007-12-25
After you suggested that maybe this is because of an error of the filesystem, I realized that ntfs-3g wasn't installed (I haven't used this laptop since february, so I didn't remember). I installed it and now it mounts automatically.

Thx for helping :)

---

