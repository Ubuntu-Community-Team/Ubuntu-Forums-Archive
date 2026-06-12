---
title: "USB Cdrw doesn't work"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by i-tech on 2005-04-13
I have an external cdrw device for my asus notebook. But i cant mount it however any advices?

---

### Post by lorap on 2005-04-13
hi friend!
i'm running warty so all you've to do is to change the device name "sr0" to "sda0".
so let's get your cdrom connected.
create any directory in your home directory:

sudo mkdir /home/yourusername/newdir

now connect your cd:

sudo mount /dev/sr0(or sda0 in your case) /home/yourusername/newdir -t vfat -o umask=000

p.s.:
that was o not zero.
if you wanna get your cd mounted each time you put cd in go to the fstab file:

sudo nano /etc/fstab

now look at the line where your regular cd is defined.create the same line as you've there for regular cd but at the right places change the device's name and path to the directory you mount it to.moreover it'd be a good idea in this case to create a directory say usb-cd in /media directory so you'd be able see it in disks folder.

---

