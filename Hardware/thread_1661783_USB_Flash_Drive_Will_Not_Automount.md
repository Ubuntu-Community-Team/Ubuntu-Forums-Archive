---
title: "USB Flash Drive Will Not Automount"
date: 2011-01-07
forum: Hardware
---

### Post by MARP1961 on 2011-01-07
I am still having problems with usb flash drives. I can only get the drive to mount and appear on the Desktop by booting with the drive already in. Also, it can only be 'safely ejected' once. Thereafter it can be mounted but not safely ejected. If I reboot with the usb inserted, again no problem. I installed 'usbmount' and it initially worked but has now reverted to the same problem.

---

### Post by Dan Z on 2011-01-07
I am having a similar problem, but only if through a hub. Even on boot up, the external hard drive will not reliably mount, even though the hub link lite is green. 

If I connect the ex hard drive direct to USB port, no problems. 

This is the third hub I have tried. 

thanks Dan

---

### Post by matt-fender on 2011-01-17
This worked for me when my USB flash drive ( NTFS ) wouldn't mount or show in fstab, unless i put it in and restarted.

Open a terminal 

paste```
sudo gedit /etc/modules
```

a text editor should open, put these two lines into that file

```
usb_storage
```
```
usbhid
```

Save the file and close it.. remove USB drive, restart. Once on desktop insert USB drive :D

---

