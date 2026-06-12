---
title: "Usb pen drive detection fails intermitently"
date: 2010-04-20
forum: Hardware
---

### Post by claracc on 2010-04-20
I have ubuntu 9.10 fully updated in a hp compaq 6720s laptop.

When I connect my usb pen drive to the laptop, the usb is detected and I can acces files to work with them, but sometimes when I am going to save files (edited with openoffice) to the pen drive, it has diappeared from the desktop.

In order to be detected again by the laptop, I have to disconnect the usb pen drive and connect it again, so now I can save files in usb since it appears in the desktop.

Why does it happens?. Is there any workaround?.

Thank you very much in advance.

---

### Post by claracc on 2010-04-22
Bump...?

---

### Post by garvinrick4 on 2010-04-22
Unusual just unmounting by itself but here is how you mount by terminal.

sudo blkid  (second letter small L)

Find its sdb1 # or sdc1 or whatever the pen drive is. It's label will be there also. If it does not have one open Disk utility or gparted in System/Admin and give it a label something simple lets say you name it flash. And it's # is sdb1.

sudo mkdir /media/flash  (Make a directory for /media/flash) (one time thing)

sudo mount /dev/sdb1 /media/flash   (mount the drive, take care of proper spacing)

sudo umount /media/flash    ( unmount that is not a typo umount is right)


This go's for any drive (dev) you want to mount.
After giving a Label drive is always mounted at /media/(label you choose)

---

### Post by claracc on 2010-04-22
Thank you very much.

Doing df -h when pen drive is connected I obtain it is mounted in /dev/sdb1.

So I understand i have to do the following to mount it again (when it umounts itself):
sudo mkdir 2C09-B916 (label of pen drive) in /media dir (I understand that I could write other label as flash or whatever, is it correct?)
sudo mount /dev/sdb1 /media/2C09-B916

I will try it next time pen drive unmounts by itself.

Regards

---

### Post by garvinrick4 on 2010-04-22
> **claracc said:**
> Thank you very much.

Doing df -h when pen drive is connected I obtain it is mounted in /dev/sdb1.

So I understand i have to do the following to mount it again (when it umounts itself):
sudo mkdir 2C09-B916 (label of pen drive) in /media dir (I understand that I could write other label as flash or whatever, is it correct?)
sudo mount /dev/sdb1 /media/2C09-B916

I will try it next time pen drive unmounts by itself.

Regards
Yes, you can Label whatever you want and your piece of Code is correct. Have a nice day.

---

