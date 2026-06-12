---
title: "System doesn't see second hard drive"
date: 2012-10-26
forum: Hardware
---

### Post by rodnower on 2012-10-26
Hello.
I have Ubuntu 12.04.1

I have 2 hard drives:

1. SAMSUNG SP80A4H
2. WD3200AAKS-75B3A0

which are recognized by BIOS, but only second recognized by the system: I have just sda...
I added pictures from BIOS and from terminal related to hard drives.
Sorry about pictures of terminal, next time just text.

I tried search in the forum but found mostly problems with USB external disk, which is far from my case.

Thanks for any advice.

---

### Post by Bashing-om on 2012-10-26
rodnower; Hi ! Welcome to the forum.

To see what the system sees on the system:
terminal command (ctl+alt+t):
```
sudo fdisk -l
```(lower case "L")
and what gets auto mounted by the system is controlled by the config file:[INDENT]/etc/fstab
[/INDENT][LEFT]See these tutorials for instruction:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

edit the file /etc/fstab to mount the drive from the desired "mount point" -attaches the drive to the file system-  with your desired mount options. Then you will have access to the drive.

Post back with any questions.[INDENT]just try'n to help <== BDQ

[/INDENT][/LEFT]

---

### Post by oldfred on 2012-10-26
The tree command shows all my drives, but the are partitioned & formatted. It really is showing partitions, not drives.

Bashing-om 's suggestion of fdisk may show drive, but unpartitioned?

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by escentrix on 2012-10-26
Are you familiar with dmesg? Does it output anything unusual about the boot up of your drives?

Edit: If you're not familiar try submitting the output of ```
dmesg | grep ata
```

---

### Post by rodnower on 2012-10-26
Thanx all for replays.
I made apt-get upgrade and after restart my system discovered second disk (now it is "sda", and main boot device became "sdb"):

```

andrey@andrey-System-Product-Name:~$ sudo fdisk -l
[sudo] password for andrey:

&#1044;&#1080;&#1089;&#1082; /dev/sda: 80.1 &#1043;&#1073;, 80059342336 &#1073;&#1072;&#1081;&#1090;
255 &#1075;&#1086;&#1083;&#1086;&#1074;&#1086;&#1082;, 63 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;/&#1090;&#1088;&#1077;&#1082;&#1086;&#1074;, 9733 &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1086;&#1074;, &#1074;&#1089;&#1077;&#1075;&#1086; 156365903 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1075;&#1086;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1075;&#1086;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
I/O size (minimum/optimal): 512 bytes / 512 bytes
&#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1076;&#1080;&#1089;&#1082;&#1072;: 0x6861f5c5

Valid partition table is missing on /dev/sda

&#1044;&#1080;&#1089;&#1082; /dev/sdb: 320.1 &#1043;&#1073;, 320072933376 &#1073;&#1072;&#1081;&#1090;
255 &#1075;&#1086;&#1083;&#1086;&#1074;&#1086;&#1082;, 63 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;/&#1090;&#1088;&#1077;&#1082;&#1086;&#1074;, 38913 &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1086;&#1074;, &#1074;&#1089;&#1077;&#1075;&#1086; 625142448 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Units = &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; of 1 * 512 = 512 bytes
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1075;&#1086;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1075;&#1086;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
I/O size (minimum/optimal): 512 bytes / 512 bytes
&#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1076;&#1080;&#1089;&#1082;&#1072;: 0x0009afc4

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sdb1   *        2048   623063039   311530496   83  Linux
/dev/sdb2       623065086   625141759     1038337    5  &#1056;&#1072;&#1089;&#1096;&#1080;&#1088;&#1077;&#1085;&#1085;&#1099;&#1081;
/dev/sdb5       623065088   625141759     1038336   82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris
 
```But the problem now is: "Valid partition table is missing on /dev/sda"...
Can I recover partition table?

---

### Post by rodnower on 2012-10-26
> **escentrix said:**
> Are you familiar with dmesg? Does it output anything unusual about the boot up of your drives?

Edit: If you're not familiar try submitting the output of ```
dmesg | grep ata
```

Thanx for replay :)
After upgrade of the system my disk discovered, now I have problem with it's partition table.

---

### Post by oldfred on 2012-10-26
If it had partition table before try testdisk.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by rodnower on 2012-10-26
Thanx!
I will try tomorrow :)

---

### Post by escentrix on 2012-10-26
You're welcome from before, glad it wasn't anything at boot honestly! oldfred is right, testdisk may be your best option. Do you know what the disk had on it before? We may be able to help more based on what type of partitions it had and how it was structured.

---

### Post by rodnower on 2012-10-27
> **escentrix said:**
> You're welcome from before, glad it wasn't anything at boot honestly! oldfred is right, testdisk may be your best option. Do you know what the disk had on it before? We may be able to help more based on what type of partitions it had and how it was structured.

Sure. It was formated for NTFS and kept ordinal windows files. It was non bootable devide and its letter was D.

I get MBR with dd and print it with hexdump.
Last records of MBR

000001b0  65 6d 00 40 00 63 7b da  c5 f5 61 68 00 40 00 40  |em.@.c{...ah.@.@|
000001c0  00 40 00 40 00 40 00 40  00 40 00 40 00 40 00 40  |.@.@.@.@.@.@.@.@|
*
000001f0  00 40 00 40 00 40 00 40  00 40 00 40 00 40 55 ea  |.@.@.@.@.@.@.@U.|
00000200

Seems that partition table didn't existed here... But it used as partitioned disk...
I will try use testdisk.

---

### Post by rodnower on 2012-10-28
OK, so this is final output of testdisk...

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <[EMAIL="grenier@cgsecurity.org"]grenier@cgsecurity.org[/EMAIL]>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9733 255 63

Current partition structure:
     Partition                  Start        End    Size in sectors


Partition sector doesn't have the endmark 0xAA55

---

### Post by rodnower on 2012-10-28
Wonderfull!
I just didn't mentioned "Quick search" in bottom of screen.
I succeed to recover MBR.

Thank you all!

---

