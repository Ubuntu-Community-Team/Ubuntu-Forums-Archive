---
title: "No boot from 9.04 iso disk image"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by eunix1 on 2009-08-14
The 32bit downloaded iso image will not boot.
Dell Inspiron 1525 (Ubuntu) supplied with 7.10 upgraded to 8.04.
The disk content can be viewed in a browser window and some packages can be loaded manually but Synaptic does not recognize the disk even though the disk is clearly listed in software sources '9.04 **'
The image was burned using Brasero (my 64 bit version took 6 tries before my video hardware was recognized but it did boot from DVD).
I have run out of ideas.  Can anyone help, please.

---

### Post by zkriesse on 2009-08-14
Post your pc "stats" or your pc hardware and software versions and type....

---

### Post by john stiles on 2009-08-14
Have you checked that the CD image is okay?

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

I also had a problem with a download of a Karma CD which sounds similar, it could be read but not booted. The image was faulty and I had to download the next days image which then all went well.

Only an idea, not a definitive solution sorry.

---

### Post by eunix1 on 2009-08-14
Intel Celeron 550@2.00GHz stepping 01.
Toshiba SATA HDD
Intel 965GM Chipset.
DVD+RW TSSTcorp TS-L632H D400 PQ: 0 ANSI: 5
2Gbit RAM
Marvell Tech Fast Ethernet
Linux  2.6.24-24-generic
 Messages in log: UDF-fs: No partition found (1)
                           ISOFS: Unable to identify CD-ROM format.
etc, etc.

---

### Post by eunix1 on 2009-08-15
Have page(s) of md5sum.txt with no errors reported??
md5sum matches perfectly.

---

