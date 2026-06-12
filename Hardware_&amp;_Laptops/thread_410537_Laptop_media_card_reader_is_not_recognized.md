---
title: "Laptop media card reader is not recognized"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by jlh68 on 2007-04-15
I have an Acer TravelMate® laptop, that is equipped with a media card reader (SD, MM and so on), that worked with that other operating system, but not Ubuntu. I removed the 40gb HD and installed a 80gbHD and installed ubuntu, so it does not have any other OS instaled.  I have enabled the wifi, been able to get email and other applications.  I do not know how to get ubuntu to recognize the media card reader. I use SD cards with my cameras and MP3 drive.  I am looking for help on this situation.

---

### Post by treesurf on 2007-04-16
If it is a TI card reader then this howto might work for you:

[http://ubuntuforums.org/showthread.php?t=315497](http://ubuntuforums.org/showthread.php?t=315497)

---

### Post by king_growler on 2007-04-16
> **treesurf said:**
> If it is a TI card reader then this howto might work for you:

[http://ubuntuforums.org/showthread.php?t=315497](http://ubuntuforums.org/showthread.php?t=315497)That's a great how-to, however all I had to do was add 'tifm_sd' to /etc/modules (and modprobe it too, so I didn't need to reboot) to get my Acer Travelmate 4500 to see the card reader... so you may want to try that first.

---

