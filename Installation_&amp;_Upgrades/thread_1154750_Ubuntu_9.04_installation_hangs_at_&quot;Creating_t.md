---
title: "Ubuntu 9.04 installation hangs at &quot;Creating the virtual disks&quot;"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by vikashtulsiyan on 2009-05-10
Hi ,
I have downloaded ubuntu-9.04-desktop-i386.iso and mounted it using Daemon Tools on my Windows Xp laptop. While trying to install as a Windows application, Ubuntu installation hangs at creating the virtual disks. This then creates wubi-9.04-rev128.log file in my temp directory whose size increases exponentially( i had to delete after it reached 1.3 Gb).

My laptop is compaq C700 2 GB ram. Please help me install ubuntu

---

### Post by vikashtulsiyan on 2009-05-10
From the log files. This is the error message that keeps repeating!!


05-10 14:16 ERROR  Virtualdisk: WriteFile() failed!
None

---

### Post by asanhost on 2009-05-16
Hello,
I have the same problem in installing ubuntu 9.04 

Would you please help me?

Yours Sincerely,

---

### Post by vikashtulsiyan on 2009-05-16
This error is preventing me from using ubuntu. any help will be greatly appreciated

---

### Post by chromas on 2009-05-17
Hi everyone,
i had this problem too. You know what was the problem caused by?
The problem occured because I tried to instal ubuntu [using wubi] on FAT32 partition!! When I cheanged the partition to NTFS everytihing went great and i have an ubuntu 9.04 now :) good luck and sorry for my bad [but not worst?] english.

---

### Post by vikashtulsiyan on 2009-05-20
So does that mean Ubuntu 9.04 doesnt support FAT32

---

### Post by vikashtulsiyan on 2009-05-22
bump

---

### Post by raymondh on 2009-05-22
> **vikashtulsiyan said:**
> So does that mean Ubuntu 9.04 doesnt support FAT32

all I can think of is FAT has a size limitation .... unlike NTSF

---

### Post by RuralHunter on 2009-07-10
> **chromas said:**
> Hi everyone,
i had this problem too. You know what was the problem caused by?
The problem occured because I tried to instal ubuntu [using wubi] on FAT32 partition!! When I cheanged the partition to NTFS everytihing went great and i have an ubuntu 9.04 now :) good luck and sorry for my bad [but not worst?] english.
Which disk need to be NTFS? I have the same problem and I launched wubi from driver E. I can see wubi tried to create virtual disk on driver C. At first the C driver is FAT32 and wubi failed when the disk file reaches 4G. So I converted driver C to NTFS and re-ran wubi. But this time wubi looks can never complete creating the virtual disk. The disk file reaches more than 14G and I had to cancel it before it filling up driver C.

---

### Post by crossx14 on 2009-11-13
This is the solution, at least for me it worked.
Download the revision 134 of Wubi, insert the LiveCD, close the LiveCD menu, then run wubi-r134.exe under Windows.
[http://people.ubuntu.com/~evand/wubi/jaunty/wubi-r134.exe](http://people.ubuntu.com/~evand/wubi/jaunty/wubi-r134.exe) 
Thank you Agostino Russo, [https://bugs.launchpad.net/wubi/+bug/386968](https://bugs.launchpad.net/wubi/+bug/386968), [https://launchpad.net/~ago](https://launchpad.net/~ago), author and maintainer of Wubi.

However, you could then have to fight with this problem:
[http://ubuntuforums.org/showthread.php?t=1166266](http://ubuntuforums.org/showthread.php?t=1166266)
[http://ubuntuforums.org/showthread.php?t=1176613](http://ubuntuforums.org/showthread.php?t=1176613)
This isn't a Wubi problem, and as far as I know, it hasn't be solved.
Best regards.

---

