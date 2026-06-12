---
title: "256GB Micro SD Card not being detected at all on my Dell Inspiron 11 3180"
date: 2019-10-21
forum: Hardware
---

### Post by josiahschuffert on 2019-10-21
So I just installed Lubuntu 18.04.3 LTS on my little Dell laptop cause I plan on turning it into a 16-Bit/41Khz mini recording rig for on the go using the low-latency kernel & KX Studio stuff. I was going to use my 256GB MicroSD card for storage but the big problem is is that anytime I install Lubuntu or Ubuntu Studio on my laptop, it doesn't detect my SD Card at all or even seemly my SD Card reader. I need to have this working cause I only have 32GB of internal space on my laptop & I plan on using both USB ports on my laptop, one for my Behringer U-Phobia UM2 & the other for this generic cheap MIDI keyboard I have. So I can't afford to only be stuck to using a Thumb Drive for storage.

I was able to get the SD Card to read when I install KX Studio 14.04 but that distro is based off an out-dated version of Ubuntu & can't support all the newest KX Studio stuff I wanna try. So I installed Lubuntu 18.04.3 instead & so far it's running good but the SD Card can't be detected. Can anyone help me here? I ran lsblk, this is what it gave me:

mcjosiah@mcjosiah:~$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0 29.1G  0 disk 
&#9492;&#9472;sda1   8:1    0 29.1G  0 part /

---

### Post by rbmorse on 2019-10-21
What format does your micro-SD card use?  If it's exfat, you probably don't have the correct driver for it.

Installing the packages exfat-fuse and exfat-utils from repository will likely fix you up.

---

### Post by tea for one on 2019-10-23
Can you boot a **live** Lubuntu session and confirm that your card reader was recognised?

---

