---
title: "mount sata drive (fat32) with fstab?"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by Crash on 2005-04-27
what i want to do is to have my sata drive
(shared betwen linux - win) to be mounted
at start up but i cant get it to work.
at start up it says special device /dev/sda5
can not be found something
when using this in fstab
/dev/sda5       /home/crash/sata  vfat    umask=000       0       0

it works perfect manualy with 
sudo mount /dev/sda5 /home/crash/sata -t vfat -o umask=000
so i dont know what im doing wrong
thx for any help on this 


copy of my fdisk -l info

Disk /dev/hda: 120,0 GB, 120000000000 byte
255 huvuden, 63 sektorer/spår, 14589 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913       14258    99169245   83  Linux
/dev/hda3           14259       14589     2658757+   5  Utökad
/dev/hda5           14259       14589     2658726   82  Linux växling / Solaris

Disk /dev/sda: 81,9 GB, 81964302336 byte
255 huvuden, 63 sektorer/spår, 9964 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               2        9964    80027797+   f  W95 Utökad (LBA)
/dev/sda5               2        9964    80027766    b  W95 FAT32

---

### Post by jackmacokc on 2005-04-27
see the post i just made..it might help [http://www.ubuntuforums.org/showthread.php?t=30233](http://www.ubuntuforums.org/showthread.php?t=30233)

---

### Post by Laemel on 2005-05-13
Mine just started doing this too... The puzzling part is that it's been working ever since I installed Ubuntu.  It's always been fine.  I rebooted a few minutes ago, and bam! - I get that same error.   fdisk -l shows it as being a normal ext3 partition, and all i have to do it $mount /home/bkivey/files-music and it mounts it fine, so I know my fstab is ok.  I didn't install any updates or change a thing before I rebooted...

Update:  I put sata_nv into /etc/modules and it works now... still no clue why it broke, but, whatever.

---

