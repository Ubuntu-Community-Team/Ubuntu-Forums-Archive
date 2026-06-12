---
title: "The live CD of Xubuntu 8.10 does not start ... and no version can be installed!"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by alepila on 2008-12-23
I have a Pentium III 600MHz with 384MB of RAM, when I try to boot from a CD of Xubuntu 8.10 Desktop, the startup screen and the bar continues to rebound until it appears black screen with a blinking text pointer at the top left. I then tried to install the alternate version of Xubuntu but when they start to install the files I leave the message that the file ... is corrupt, click continue and tells me that another file and corrupt and so on until it tells me that the installation can be completed. I check the CD and I do not find errors ... I then tried to install Ubuntu alternate but again errors so corrupted files. until, in this case I leave the message that the installation can be completed. I tried to burn the CD at low speed by another PC and download another ISO image but nothing to make the installation is never finished, I tried to start the recorder as the master instead of the DVD player but nothing to do ... still the same story, you can not complete the installation. Then I try to download alternate Xubuntu 8.10, verify the integrity of the ISO, burn, check the integrity of the CD ... all OK. I try to install and yet the same mistakes in reading. Why is this happening?

---

### Post by Pumalite on 2008-12-23
Did you do md5sum on the iso? Do not use CD-RW
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by alepila on 2008-12-23
Yes i do md5sum and i didn't use CD-RW

---

### Post by Pumalite on 2008-12-23
Have you tried the Xubuntu Alternate CD?:
[http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/)

---

### Post by Kevbert on 2008-12-23
Welcome to Ubuntu.
Have you tried a memory check ? (memtest in the menu, as it's possible to run Windows with faulty memory - random crashes occur).

---

### Post by alepila on 2008-12-24
Kubuntu doesn't run with 384Mb RAM

---

### Post by alepila on 2008-12-24
Thank's i try to run memtest

---

### Post by Pumalite on 2008-12-24
If you have found nothing; including memtest: try cleaning up your hard drive. Get Gparted Live CD, reformat and reinstall everything.

---

### Post by alepila on 2008-12-24
I have done memtest, the result was "no errors", i have cleaned my hard disk and i tryed to reinstall Xubuntu but nothing...

---

### Post by CRIMPS on 2008-12-25
You are not the only one having this problem.  I was using a cd-RW, so I burned to a different disk format.  I was using the Ubuntu 8.04 Alternate cd.  I also used GPartEd to format the entire disk.

The computer is a:
P4 1.6Ghz
256MB RAM

Anyone have any other ideas for solving these installation issues?

Thanks
Z

---

### Post by Pumalite on 2008-12-25
With your RAM; use the Alternate CD Xubuntu

---

### Post by paddy1 on 2008-12-25
I had the same problem, and ran Gparted, and no longer have a problem

---

### Post by alepila on 2008-12-28
nyone have any other ideas?

---

### Post by CRIMPS on 2008-12-28
I was able to succcessfully install Ubuntu 8.04 via the Alternate CD.  I really think the problem was the way in which the .iso was being burned.  I originally used a cd-rw.  The next time I burned the image to another cd, that cd was also suspect.  I burned the image to a fresh cd-r and was then able to finish the install.

Try burning the image to a new cd-r.

Good luck.

---

### Post by alepila on 2008-12-29
I burned the image to another cd but i can't finish the install

---

### Post by Sour Mash on 2008-12-29
I installed 8.04.1 and that got round the issue, of course I then upgraded to 8.10 and messed it up, I am back tothe blinking screen of bemusement!

---

