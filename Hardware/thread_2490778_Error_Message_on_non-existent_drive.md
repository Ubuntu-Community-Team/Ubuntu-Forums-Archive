---
title: "Error Message on non-existent drive"
date: 2023-09-15
forum: Hardware
---

### Post by sleighton on 2023-09-15
Trying to understand  why I am getting this error message on a non-existent drive, there is no sdf device on this system that I can find. 

Sep 15 06:39:47 plex-hh kernel: [3331115.290384] Buffer I/O error on dev sdf1, logical block 1280796114, async page read

Any advice on where to look?

Scott

---

### Post by yancek on 2023-09-15
What did you do to get that message?  Run a specific commamd?  Trying to access a specific location on the computer?  Some other option?

---

### Post by sleighton on 2023-09-15
Nothing at all, it is showing up in my logwatch report daily now. I did notice that my drives go from sda - sde, then skip sdf and start again at sdg - sdh. There are six usb drives connected and one internal sata, so all seven drives are accounted for. 

Scott

---

### Post by yancek on 2023-09-16
>  I did notice that my drives go from sda - sde, 

Is that using fdisk, gdisk or similar software?  Did you previously have a disk that showed at sdf?  The link below discusses a similar problem.  Don't know if it helps so I'm all out of guesses.

[https://unix.stackexchange.com/questions/279618/determine-affected-file-given-logical-block-number](https://unix.stackexchange.com/questions/279618/determine-affected-file-given-logical-block-number)

---

### Post by sleighton on 2023-09-16
fdisk -l does not show a drive at sdf, it does show sda - sde, sdg-sdh. I honestly can't remember if I ever had a drive on sdf, but the utilities mentioned at the stackexchange link all do not recognize sdf as a drive nor does sdf show up in /dev

$ ll /dev/sd*
brw-rw---- 1 root disk 8,   0 Aug 24 21:40 /dev/sda
brw-rw---- 1 root disk 8,   1 Aug 24 21:40 /dev/sda1
brw-rw---- 1 root disk 8,  16 Aug 24 21:40 /dev/sdb
brw-rw---- 1 root disk 8,  17 Sep 15 16:50 /dev/sdb1
brw-rw---- 1 root disk 8,  32 Aug 24 21:40 /dev/sdc
brw-rw---- 1 root disk 8,  33 Sep  5 21:32 /dev/sdc1
brw-rw---- 1 root disk 8,  48 Aug 24 21:40 /dev/sdd
brw-rw---- 1 root disk 8,  49 Sep 15 21:59 /dev/sdd1
brw-rw---- 1 root disk 8,  64 Aug 24 21:40 /dev/sde
brw-rw---- 1 root disk 8,  65 Sep 16 04:57 /dev/sde1
brw-rw---- 1 root disk 8,  96 Aug 24 21:40 /dev/sdg
brw-rw---- 1 root disk 8,  97 Sep  7 17:49 /dev/sdg1
brw-rw---- 1 root disk 8, 112 Sep 10 21:00 /dev/sdh
brw-rw---- 1 root disk 8, 113 Sep 15 04:03 /dev/sdh1

---

