---
title: "Safe USB harddrive mounting"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by muskyminxx on 2006-09-03
Like many people, I am trying to  mount a USB hard drive and have it work most of the time.  I used gparted to reformat it as ext3, and when I plug it into my usb slot  an icon shows up on the (KDE) desktop.  Unfortunately, when I try and read or write to it, I get a permissions error. I know that I can run everything as root and have access to it, but that does not seem to be the best answer. How can I  make this drive always mount with user permissions?

---

### Post by mssever on 2006-09-03
If you don't care about automounting, you can do the following:[LIST=1]
[*]Find the device name for your partition. I'll use /dev/sda1 as an example. Also, change any other example info to suit your needs.
[*]sudo umount /dev/sda1
[*]sudo e2label /dev/sda1 USB_HD
[*]make the following entry in /etc/fstab:
```
LABEL=USB_HD /media/USB_HD ext3 defaults,users 0 2
```
[*]sudo mkdir -p /media/USB_HD
[*]sudo mount /media/USB_HD
[*]If that doesn't fix it by itself, do ```
sudo chmod 777 /media/USB_HD
```[/LIST]

---

### Post by muskyminxx on 2006-09-04
Thanks for the reply.  I kind of would like the automount to work.  Right now it automatically recognizes the drive and automatically makes it have root only permissions.  Can't I just change something to make it automatically recognize the drive and automatically give it user permissions?

thanks

---

### Post by mssever on 2006-09-04
Automounting in Ununtu is handled by pmount, I believe. I don't really know much about pmount, though. You can try man pmount, and if you need more help, you might Google pmount.

---

