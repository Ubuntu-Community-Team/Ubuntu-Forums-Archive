---
title: "Re: Missing print drivers, corrupted filesystem."
date: 2016-05-22
forum: Hardware
---

### Post by thenh813 on 2016-05-22
EDIT: Got a new question now. My Ubuntu install just broke itself. 

Original Question:
I am having trouble installing my printer on Ubuntu 16.04 (Xenial) 64 bit. It is a new install. The driver for the Canon ip1800 series printer is not listed under models on the add printer menu. Pretty much EVERY other model, including the ip2000 series and printers before the ip1800 series are listed. I know there's a ppa for cnijfilter, but it has no packages for Xenial. No, the drivers for 14.04 from that ppa do not work because of library version incompatibilities. The cups filters for the ip2000 series should work as they're built from the same or very similar version. Can someone provide me with the *.ppd file, any additional filters/drivers and correct settings?

---

### Post by thenh813 on 2016-05-23
Turned my PC on and it hung at "Searching for BTRFS Filesystems".
The  filesystem corrupted itself and can't be mounted or repaired.
I guess it's reinstall then, what a pain I just got all my applications installed.
At least I put /home elsewhere so I  don't have to restore a backup.
Also, I installed updates before turning off last night if that helps.
Maybe the new initrd it generated did something bad???

---

