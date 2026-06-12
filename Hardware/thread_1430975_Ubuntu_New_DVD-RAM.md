---
title: "Ubuntu New DVD-RAM"
date: 2010-03-16
forum: Hardware
---

### Post by VeGeTa-X on 2010-03-16
I just bought a new lightscribe dvd-ram (ad-7580A) for my dell d505 and I just put in my dell laptop I see the dvd rom drive light up and it opens also but when I go to my computer a double click on the dvd rom icon nothing happens please let me know what steps I have to do when install a new drive on a ubuntu computer. Thx

---

### Post by Fafler on 2010-03-16
It's most likely a hardware issue. Is the drive detected by the BIOS?  Did you have a drive in the laptop before and did it work? To see if the kernel detects the drive, open a console and type```
fafler@r50:~$ dmesg | grep CD-ROM
[    1.107198] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8082N 0K03 PQ: 0 ANSI: 5
[    1.120949] Uniform CD-ROM driver Revision: 3.20
[    1.121068] sr 1:0:0:0: Attached scsi CD-ROM sr0
fafler@r50:~$
```

---

### Post by VeGeTa-X on 2010-03-16
For some reason weird this morning it works go figure.  Well thx for you help

---

