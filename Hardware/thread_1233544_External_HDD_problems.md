---
title: "External HDD problems"
date: 2009-08-06
forum: Hardware
---

### Post by Zepar on 2009-08-06
I am trying to use my external hard drive, but when I plug it in and connect it to my laptop nothing happens. Usually it takes a bit to connect, but now it isn't connecting at all. I checked, and my computer does read it, however, I assume it is unable to mount it, and it doesn't even show up in the Computer folder. I checked /dev/disk/by-id and it reads it as "usb-WD_2500JB_External_57442D574D414E4B32353137343337-0:0" and "usb-WD_2500JB_External_57442D574D414E4B32353137343337-0:0-part1" neither of which I am able to open. I tried several lines of code in the terminal, including
```
sudo mkdir /media/usb
sudo mount -t vfat /dev/sda1 /media/usb
```
the problem is that everywhere i've looked, people's EHDD's are visible in the Computer folder, but not mountable, where mine is not. I am completely lost... please help.

---

