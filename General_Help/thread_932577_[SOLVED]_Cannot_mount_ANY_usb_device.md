---
title: "[SOLVED] Cannot mount ANY usb device"
date: 2008-09-28
forum: General Help
---

### Post by itix on 2008-09-28
Hi. I have just aquired an Eee PC 901 and as with my 701, I hated the default xandros and replaced it with ubuntu. This time I choose regular ubuntu and not xubuntu and it has up until now been a complete disaster due to one thing, namely the mount feature. I managed to mount my brothers usb stick for a fleeting moment by formatting it to ext3 and threw the drivers for wireless internet on to it. It now has working wireless (but not ethernet) and all the other common fixes, but i still miss all my files from my previous computer...

It usually throws me a message saying invalid mount options and when I resolve to commandline, it says

>        wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by zzzzz1 on 2008-09-28
Open your fstab file:
```

sudo gedit /etc/fstab
```

Find and comment out (by adding a # to the beginning of the line) the line referencing /media/cdrom. Reboot, and you should now be able to use SD and USB again.

fro here  [http://tombuntu.com/index.php/2008/09/01/installing-ubuntu-804-on-the-eee-pc-901/](http://tombuntu.com/index.php/2008/09/01/installing-ubuntu-804-on-the-eee-pc-901/)

---

### Post by itix on 2008-09-28
Thanx :D

Why oh why didn't I think of that?

---

### Post by zzzzz1 on 2008-09-28
if you install the custom eee kernel you should get both, Ethernet and wifi working

---

### Post by itix on 2008-09-29
I know. I have the custom kernel installed. I managed to install the driver for the wireless and installed the custom kernel trough the array.org repositories.

Everything is working like a charm here (except the keys above the Fbuttons and the x11 output module in VLC ;) )

---

