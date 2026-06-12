---
title: "Mulish microSD card"
date: 2014-10-19
forum: Hardware
---

### Post by luca2014 on 2014-10-19
I hope i chose right section. Here is the deal:

I have SanDisk 64gb microSDXC card (seems to be exFAT) and used it for almost a year in my Xperia Tablet Z on stock roms and everything worked fine.
About week ago i safetly removed it (I think so.) from tablet and instead of it I put in microSD from my cm11.0 phone (this part may be irrelevant).
After coping some music i change it back and find out I can no longer write to 64gb SD (neither file managers, nor camera)
I'm aware of Android 4.4 problem with sd cards, so i thought it is all due to File Commander update (back then I had no root)
Today i had some to time to investigate it and made root access, istalled neccesery patches, but nothing happend.
I search a lot of forums and tried few stuff, but none of it helped:

Under Windows: I tried clearing readonly attributes, but I wasn't able to finish formating it with windows tools and formatter v4 showed write-protection. I was able to access files, so everything is backuped. 

Under Ubuntu: After installing all possible eXFAT drivers it was able to read that my tablet's SD. Here comes the part I got lost, because of lack of knowledge:

I typed: sudo dosfsck -a /dev/sdc1

> fsck.fat 3.0.26 (2014-03-07)
Logical sector size is zero.


Seems disturbing.

I tried Gparted, but no result due to lack of exFAT support.

Then I typed: sudo fdisk -l

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 38913, w sumie sektorów: 625142448
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0x1549f232

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sda1   *          63   609811334   304905636    7  HPFS/NTFS/exFAT
/dev/sda2       609811335   625137344     7663005    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 121601, w sumie sektorów: 1953525168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 4096
Rozmiar we/wy (minimalny/optymalny) w bajtach: 4096 / 4096
Identyfikator dysku: 0x551737fb

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sdb1            2048  1534091263   767044608    7  HPFS/NTFS/exFAT
/dev/sdb2      1534093310  1953523711   209715201    5  Rozszerzona
Partycja 2 nie zaczyna si&#281; na granicy bloku fizycznego.
/dev/sdb5      1534093312  1542090751     3998720   82  Linux swap / Solaris
/dev/sdb6      1542092800  1953523711   205715456   83  Linux

Disk /dev/sdc: 63.9 GB, 63864569856 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 7764, w sumie sektorów: 124735488
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0x00000000

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sdc1           32768   124735487    62351360    7  HPFS/NTFS/exFAT

Then tried: sudo mkfs.exfat -n EXTERNAL /dev/sdc1

> mkexfatfs 1.0.1
Creating... done.
Flushing... done.
File system created successfully.


Then: sudo fsck.exfat /dev/sdc1

> exfatfsck 1.0.1
Checking file system on /dev/sdc1.
File system version           1.0
Sector size                 512 bytes
Cluster size                128 KB
Volume size                  59 GB
Used space                 2688 KB
Available space              59 GB
Totally 0 directories and 0 files.
File system checking finished. No errors found.

Seems formatted? Nope. Files are still there and are accessible...

Tried to format it in tablet, cm11.0 phone, even deleting files from file manager in ubuntu, but result never was permanent...

I hope i recreated all my steps.

Is there anything I can do with it?

---

