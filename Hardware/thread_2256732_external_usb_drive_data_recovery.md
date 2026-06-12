---
title: "external usb drive data recovery"
date: 2014-12-14
forum: Hardware
---

### Post by dkdias on 2014-12-14
I used my fantom 2 tb drive to do a system backup on my new laptop. The system backup changed the format on the Drive from NTFS to fat32. I lost everything on the drive. I know it was stupid.  I mainly care about the photos I lost. I bought a program to do this but it did not work. .... Please help me recover the pictures I lost. Thank you!

---

### Post by sudodus on 2014-12-14
Please do not mount the drive. Do not use it at all until you start according to a plan to rescue the data.

The system backup maybe overwrote some of your pictures, but chances are that a lot of the picture data are still sitting on the drive surface. If you are really concerned, I suggest that you make a cloned copy of the drive, and do the recovery operations on that drive. It means that you need at least two more drives, the target drive for the cloning, and a target drive for the recovered picture files.

If this is too much trouble or cost, you need to be extra careful.

Boot from another drive (not the one with the pictures). Install ***testdisk and photorec***, described and available at

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Try first with testdisk, which might restore your previous file system. If it does not work, try with photorec, which can recover files from the data (identifying typical file headers for various types of files). Focus on one kind of file each time, otherwise you will drown in files.

---

### Post by dkdias on 2014-12-15
Thank you! I will give it a shot...............

---

### Post by dkdias on 2014-12-20
When I try to run testdisk, my antivirus stops it from running? I used the links you gave me to download  the program?

---

### Post by sudodus on 2014-12-20
Then I suggest that you switch off the antivirus program. If you do not trust testdisk (and implicitly my advice), you could still try photorec, but if that program is also detected by your antivirus program I have no more advice. In that case, let us hope someone else will chip in and help you.

---

### Post by Mark Phelps on 2014-12-21
Since the drive was formatted NTFS, you may have better results using Windows data recovery apps instead of Linux.

To do that, you would need to do the following:
1) Connect your drive to a working Windows PC
2) Download and install "recuva" on the PC
3) Run recuva and see what it finds.

---

