---
title: "iso md5sum ok, individual file md5sum not ok"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by asynchronous13 on 2008-12-04
I downloaded 8.10 server, checked the md5sum on the .iso file and it matched. But on installation I got an error. 

Checked the md5sum of the files on the burned CD:

./install/netboot/pxelinux.cfg/default: Not a directory
./install/netboot/pxelinux.cfg/default: FAILED open or read
./install/netboot/pxelinux.0: FAILED

So I tried again -- downloaded 8.10 server from a different mirror, again checked the md5sum of the .iso, and it checks out fine. 

Burned the cd and double-checked the md5sum of the files, got the same error as above. Both of these files are 0 byte files on the CD. 

Searching the forums turns up this error several times, but no real solution is offered.

2005
[http://ubuntuforums.org/showthread.php?t=37916](http://ubuntuforums.org/showthread.php?t=37916)
[http://ubuntuforums.org/showthread.php?t=19228](http://ubuntuforums.org/showthread.php?t=19228)
[http://ubuntuforums.org/showthread.php?p=302532](http://ubuntuforums.org/showthread.php?p=302532)
[https://lists.ubuntu.com/archives/ubuntu-users/2005-June/039378.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-June/039378.html)

2006
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg35096.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg35096.html)

2007
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg572282.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg572282.html)

I'm not sure how the downloaded .iso md5sum is good, but then the burned CD md5sum fails (but only for 2 files). I'm using WinXP pro sp3, burning with CDBurnerXP Pro 3, cd drive is a Sony CDRW/DVD CRX830E, burning to CD-R. Using Cygwin for md5sum. Thoughts or help would be appreciated.

---

### Post by taurus on 2008-12-04
How fast did you burn the ISO image?  If you used the default speed, try burning it again with a slower speed like 4x.

---

### Post by gpsmikey on 2008-12-04
Couple of things come to mind -- I have had problems with bad media before and you may be seeing that sort of issue - try a different batch/brand of media (and burn slow).  You might also try doing it with my favorite utility (free !! ) imgburn - runs very well under XP -- make sure you check the box to verify after burning - it will burn the CD then go back and read it to verify all is well.  Listen for the drive to start "hunting" (speeding up/down etc) when it runs into a problem area on the disk.  With the disks I use (Taiyo Yuden), a verify starts and it reads at a constant speed all the way through. 

[http://www.imgburn.com](http://www.imgburn.com) 

mikey

---

### Post by asynchronous13 on 2008-12-05
Well, this is odd.

Computer 1 - WinXP laptop
Computer 2 - to become home server
CD1 - first download and burn
CD2 - 2nd download and burn

First, CD1 failed to install Ubuntu server on Computer 2. Ubuntu Disk check revealed errors. md5sum of CD1 on Computer 1 revealed errors. md5sum of .iso on Computer 1 was ok. 

Next, re-download iso (just to be sure). md5sum on 2nd iso checks out. md5sum of CD2 reveals errors, again.

I decided to try and install anyway. Ubuntu Disk check of CD2 on computer 2 passed! So I installed anyway, and CD2 works. 

Both CDs have the exact same md5sum errors on my laptop, but on the other computer, CD2 passes and CD1 fails.

Odd.

---

### Post by psusi on 2008-12-05
What speed did you burn the disks at?  Years ago I used to see problems with reading a cd in an older slower reader than the speed the cd was burned at.  Like trying to read a cd in an older 4x reader that was burned at 8x.

---

