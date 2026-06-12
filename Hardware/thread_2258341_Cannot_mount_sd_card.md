---
title: "Cannot mount sd card"
date: 2014-12-26
forum: Hardware
---

### Post by michael238 on 2014-12-26
I have a new sd card which I can't mount.

In Disks, I see the drive as Multiple Card Reader, but Volumes shows "no media" and I cannot perform any functions on it.

GParted does not show it at all.

I'm stumped. Please help. Thanks.

---

### Post by weatherman2 on 2014-12-27
What kind of card is it?  Is it an SDXC card?  (Newer style?)  If the card is larger than 4GB, it is probably SDXC - and the default format is probably exFat, which Ubuntu will support with a driver:

[http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04](http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04) 

(See the first answer.)

However, if you have a laptop with an internal card reader, it may not work still.  My Acer laptop with Ubuntu 12.04 does not read my exFat SDXC card in the internal SD card reader.  It will read it with a USB SD reader.  Also, I can read the exFat card in the internal card reader with Windows 8.  Probably a driver can be fixed somehow - but it doesn't work automatically for me.  Maybe it will in Ubuntu 14.04.

---

### Post by michael238 on 2014-12-27
Thanks for your reply weatherman. I'm gonna consider this closed because I plugged the card into a windows machine and it didn't recognize it either so there is probably some other issue with the card.

---

### Post by Bucky Ball on 2014-12-27
> **michael238 said:**
> Thanks for your reply weatherman. I'm gonna consider this closed because I plugged the card into a windows machine and it didn't recognize it either so there is probably some other issue with the card.

I'd say faulty card. I have used SD cards of all capacities (larger than 4Gb) since 8.04 and never an issue. Faulty card, perhaps.

You can mark the thread as solved by following the second link in my signature. Good luck with it all. ;)

---

