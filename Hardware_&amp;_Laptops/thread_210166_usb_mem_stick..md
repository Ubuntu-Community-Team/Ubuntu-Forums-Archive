---
title: "usb mem stick."
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by mbgb14 on 2006-07-06
I've just plugged in my new USB stick that I bought off of a fellow LUG'er. It was still vacuum sealed in the case, and works fine under windows.

But, when I plug it into Linux, the little led comes on for a sec, dissapears, and there's no trace that its connected. I can't use it at all.

Its this one

[http://www.sandisk.com/Products/Catalog(1168)-NEW__SanDisk_Cruzer_Micro_USB_Flash_Drive.aspx](http://www.sandisk.com/Products/Catalog(1168)-NEW__SanDisk_Cruzer_Micro_USB_Flash_Drive.aspx)

Any suggestions??

---

### Post by ahaslam on 2006-07-06
[QUOTE=mbgb14]I've just plugged in my new USB stick that I bought off of a fellow LUG'er. It was still vacuum sealed in the case, and works fine under windows.

But, when I plug it into Linux, the little led comes on for a sec, dissapears, and there's no trace that its connected. I can't use it at all.

Its this one

[http://www.sandisk.com/Products/Catalog(1168)-NEW__SanDisk_Cruzer_Micro_USB_Flash_Drive.aspx](http://www.sandisk.com/Products/Catalog(1168)-NEW__SanDisk_Cruzer_Micro_USB_Flash_Drive.aspx)

Any suggestions??[/QUOTE]

Try, **sudo modprobe -r ehci-hcd**
If it works, format the drive & it may be ok in the future.

If that doesn't work, have a read through this thread:
[http://ubuntuforums.org/showthread.php?t=191963]("http://ubuntuforums.org/showthread.php?t=191963")

Good look, I had similar problems in Breezy, changing the permissions & formatting it sorted me back then.

Tony.

---

### Post by mbgb14 on 2006-07-06
Got it working. I just rebooted. Strangely, it works now all the time. 
Tx though.

---

### Post by macozz on 2006-07-07
I posted a similar, but not exactly the same, problem at [http://www.ubuntuforums.org/showthread.php?t=210186](http://www.ubuntuforums.org/showthread.php?t=210186)
I reformated the pen drive to Fat32 (was Fat16, originally) but nothing happens anyway.
The funny thing is that the pen drive is recognized if I boot the computer with it plugued, but not if I plug it after the computer is already on, nor (even more strange) if I reboot the computer with it pluged!
Also, if when it gets recognized after a boot I umount it, the system does not recognize it anymore... ](*,) 
A large variety of usbdevices worked fine on the same computer/system, this is the very first time I have a problem like this.
Help please!

Cheers

---

