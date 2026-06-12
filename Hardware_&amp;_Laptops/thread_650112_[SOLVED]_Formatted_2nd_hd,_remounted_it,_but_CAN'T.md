---
title: "[SOLVED] Formatted 2nd hd, remounted it, but CAN'T USE IT!!"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by rabbix2 on 2007-12-25
Formatted my newly "found" 2nd hd, remounted it, and: I CAN'T USE IT!!! What do I do now?

---

### Post by logos34 on 2007-12-25
More info needed.

---

### Post by taurus on 2007-12-25
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by rabbix2 on 2007-12-25
I used my 2 internal harddisks, with dapper on the 1st. I unplugged the 2nd and upgraded to edgy on the 1st (/dev/sda). Plugged in the 2nd hd (/dev/sdb). First I didn't find it, but with help from the forum I mounted it in /media/sdb1, and I have it on my desktop too. But I cannot make files in it, and I cannot open the "lost and found", I am told I don't have the authorization (or something like that) to open it.
The /dev/sdc is my external hd, and with that no problem at all.

Some more info:

root@gurkan-desktop:~# ls -la /media/sdb1
totalt 24
drwxr-xr-x 3 root root  4096 2007-12-26 03:03 .
drwxr-xr-x 5 root root  4096 2007-12-26 03:46 ..
drwx------ 2 root root 16384 2007-12-26 03:03 lost+found

root@gurkan-desktop:~# sudo fdisk -l

Disk /dev/sda: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9729     3196935    5  Utökad
/dev/sda5            9332        9729     3196903+  82  Linux växling / Solaris

Disk /dev/sdb: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 40,0 GB, 40020664320 byte
255 huvuden, 63 sektorer/spår, 4865 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdc1               1        3295    26467056    b  W95 FAT32


root@gurkan-desktop:~# df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda1              71G   66G  963M  99% /
varrun                633M   88K  633M   1% /var/run
varlock               633M  4,0K  633M   1% /var/lock
procbususb             10M  124K  9,9M   2% /proc/bus/usb
udev                   10M  124K  9,9M   2% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   18M  615M   3% /lib/modules/2.6.17-12-386/volatile
/dev/sdb1             230G  189M  218G   1% /media/sdb1
/dev/sdc1              26G   16G  9,7G  62% /media/IOMEGA_HDD
root@gurkan-desktop:~#

---

### Post by taurus on 2007-12-25
All you have to do is to change the ownership of /media/sdb1 from root to your login name.  _Assuming_ your login name is **rabbix**, run

```
sudo chown -R **rabbix**:**rabbix** /media/sdb1
ls -la /media
```
You should be able to write to /media/sdb1 anytime you want now.

p.s.  You need to edit /etc/fstab and remove the last line, /dev/sdb5, because you have already removed that partition.  So, there is no such thing as /dev/sdb5 anymore.

---

### Post by rabbix2 on 2007-12-25
Here's the rest:

root@gurkan-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=617eafa7-2029-4226-93cf-c6e230d830ac / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=3634532d-5b40-4b45-ab09-4195e22918ef none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
/dev/sdb5   none   swap   sw   0   0

---

### Post by rabbix2 on 2007-12-25
YES!!!!
That DID IT! =D>
I did suspect it had to do with "permissions".
THANKS A LOT!
In spite of (or - rather - just because of) ]constantly stumbling into new "problems" as soon as I've fixed "the previous one" I'm growing more and more fond of my Ubuntu and the Linux world. As a matter of fact, I finally removed my windowsXP yesterday, and I feel great :)

---

