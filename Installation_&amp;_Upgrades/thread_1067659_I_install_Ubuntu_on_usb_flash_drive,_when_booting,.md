---
title: "I install Ubuntu on usb flash drive, when booting, I have error 17"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Kang Long on 2009-02-12
I install ubuntu on usb flash drive( transcend v33 4GB), extractly as this page say:
```
http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/
```
[http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)
Everythings seem to be okay, and when I boot from usb drive, I see grub menu. but if I choose option Ubuntu 8.04( or other option), it tells me: error 17: can't mount partition.
how to correct it? thanks

---

### Post by caljohnsmith on 2009-02-12
OK, when you get the Grub menu on start up, how about selecting the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

