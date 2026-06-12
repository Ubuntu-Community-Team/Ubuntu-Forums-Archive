---
title: "Ubuntu on Acer Aspire One - USB issue"
date: 2008-09-15
forum: Hardware
---

### Post by drdivad on 2008-09-15
After installing Ubuntu and getting the update/upgrade files through the terminal, I am getting errors regarding USB devices (specifically USB sticks and USB External Hard Drives).

My USB mouse works perfectly, however once I plug in my hard drive, it appears in the Places drop-down menu as WD Passport with a USB sign. However after a few seconds I get the following error:

> Cannot mount volume
Invalid mount option when attempting to mount the volume 'WD Passport.

thanks for the help guys.

---

### Post by BigRD on 2008-09-23
I had exactly the same problem and have managed to solve it in my case.

Whenever I connected the drive I would get an error saying cannot mount but could mount the drive manually.  I checked fstab and noticed that "sdb" was set as cdrom0 and would try to mount as a cdrom drive - obvious problem there! I edited fstab and changed the sdb to sdc. This should mean I can still attach an external cdrom and if the Ubuntu defaults are still set to automatically detect USB drives then this will hopefully solve it for you too. For me the drive now appears in Ubuntu Netbook Remix with the eject symbol to safely disconnect without browsing to the drive and unmounting.

gksu gedit /etc/fstab

find the following line

/dev/**sdb **  /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0

change to:

/dev/**sdc ** /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0

Save and reboot. Plug in your drive...fingers crossed :)

---

### Post by fdimmling on 2008-09-23
> **BigRD said:**
> 

gksu gedit /etc/fstab

find the following line

/dev/**sdb **  /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0

[...]

IMHO you should just comment it out. It is a common problem with computers without a buildin cdrom drive.

Friedrich

---

### Post by a1ygator on 2008-09-23
Awesome! This solved the problem, thanks.:KS:guitar:

---

### Post by amj on 2008-09-27
There's a great summary for Ubuntu on an Aspire One [here]("https://help.ubuntu.com/community/AspireOne"), including your USB mounting matter.

---

