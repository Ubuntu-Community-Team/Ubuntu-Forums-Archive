---
title: "reinstall error urgant"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by halJ on 2009-07-31
Hello,
 due to some problems i have been forced to reinstall Ubuntu.
I burned a cd of the alternate installer and booted it up. before i started the reinstall i asked it to check the disk for defects. it passed and i proceeded with installing. once it got to select and install software it started complaining about corrupt files and that it could not proceed or to go to the menu and try again.i did and it again failed. i then burned a new cd and tryed again. same problem. i burned a third cd and used it with the same problem. Is there something i am missing or doing wrong?


Also, the .iso that i used for the cd's i confirmed to be intact with MD5 and SHA-1. the burned cds i verifyed against the .iso and they passed. I burned the cds on a differant computer than the one i am installing on

---

### Post by tommcd on 2009-08-01
How are you burning the CDs? If you are burning from Ubuntu, simply right-click on the iso image and choose "write to disc". If you are burning the CD from windows, use Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Whatever way you burn the CD, be sure to burn it at the slowest possible speed.
Also, just to rule out a corrupted download, I would download the alternate CD iso again. This time choose a different mirror.
It seems odd though that the "check disk for defects" test would pass, yet the installer still complains about corrupted files. The only other thing I can think of is that your CDROM drive is faulty, or the lens is dirty, and it is just not reading the CD correctly.

---

### Post by Sef on 2009-08-01
Sometimes too the disks can be bad, so try buying some different ones, if the problem persists.

---

### Post by presence1960 on 2009-08-01
> **Sef said:**
> Sometimes too the disks can be bad, so try buying some different ones, if the problem persists.

I have had problems with memorex CDs. They just don't seem to work when making bootable CDs. They work fine for data,

---

### Post by halJ on 2009-08-01
TOMMCD: i was useing Imgburn. a iso burning program.
you may be right about faulty cd drive though because today i found the original cd i installed from(though it was an older version) and tried to reinstall with it and it again failed from corruption Though i know for a fact that it works.

SEF/PRESENCE1960: all the CD's were from one package of Memorex(except the original old install CD). I will buy a differant brand of CD's and see if they work.


How do you clean the CD drive if that is a problem?

---

### Post by tommcd on 2009-08-02
> **halJ said:**
> 
How do you clean the CD drive if that is a problem?
If the lens is not visable when you eject a CD, like it is in many laptops, then there is no easy way as far as I know. You could try shooting some compressed air into the drive, but I doubt that would do anything.
See these:
[http://www.howtodothings.com/computers/a3631-how-to-clean-a-cd-rom-drive.html](http://www.howtodothings.com/computers/a3631-how-to-clean-a-cd-rom-drive.html)
[http://www.ehow.com/how_2044857_clean-cdrom-drive.html](http://www.ehow.com/how_2044857_clean-cdrom-drive.html)
[http://www.computerdust.com/clean_computer/clean_cd_rom_drive.html](http://www.computerdust.com/clean_computer/clean_cd_rom_drive.html)

---

