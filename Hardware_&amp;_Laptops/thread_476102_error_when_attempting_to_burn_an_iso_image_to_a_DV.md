---
title: "error when attempting to burn an iso image to a DVD"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by tvphil on 2007-06-16
I believe this is a hardware problem, so I hope I'm in the right forum. First the truth, about a week ago a DVD wouldn't come out (un mount)and I held the open button down while I re-started to get it out. I say this, because I think this may have been what caused the problem I'm having now. When attempting to burn a video to a DVD, I get as far as the iso image beginning to burn, then I get the following error and I end up with a coaster....

Burning
Executing 'genisoimage -dvd-video /home/tvphil/dvd/ | builtin_dd of=/dev/dvd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/dvd: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=10h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument
/dev/dvd: flushing cache
/dev/dvd: updating RMA
/dev/dvd: closing disc

What does this indicate? If it is a mounting problem, how do I correct it and make it normal again? I'm using Ubuntu Feisty (7.04) with the latest updates. I've tried 3 different DVD burning programs,DVDStyler, Gnome Baker in combo with DeVeDe and the default Gnome cd/DVD Creator, it happens with all 3, with the same error. Also, prior to my DVD stuck-in-the -tray episode a week ago, I had no problem burning CD's or DVD's.

---

### Post by tvphil on 2007-06-17
Just a follow up to my last posting. After some research, it appears to be a problem with the address of the DVD drive. Also, the burner reads fine, the problem is only with writing. Finally, it both reads and writes fine on the Windows partition of the same hard drive, so it's not a hardware issue.

---

### Post by L337reap0r on 2007-07-09
I'm seemingly having this same problem. I'm currently running 7.04, fully updated, with a LiteOn DVD drive. I had previously had Dapper installed, and I had the same issue. I never did any manual configuration of the drive, because it read fine by default and I don't know how.

No burning tool that I've tried has successfully gotten past starting to write the disk. Sadly, my new install of Feisty (love it, btw) somehow broke my windows install so I can't just flip over and burn it there. 

While I'm still a Linux noob, the concept of bad addressing sounds like a good guess to me, but I have no knowledge of how to go about fixing it.

---

### Post by azraelck on 2007-07-09
Interesting, does this only happen when burning ISO's onto a DVD-R or can you burn them onto CD-R's as well? What about music CDs, or regular data discs? If it's burning those, then it might be a driver issue. 

I had the same problem with the drive not un-mounting after playing HOMMII for a spell in WINE; the disc wouldn't eject so I had to reboot and eject it while loading. However, afterwards it burned a music CD fine; but I also don't have any ISO's to burn, or a DVD-RW, I just have the DVD/CD-RW combo-drive (and a regular DVD). So I cannot try to duplicate your problem (and probably couldn't regardless, sue to hardware differences). Good luck.

---

### Post by lisati on 2007-07-09
You can burn some ISO files on both DVD and CD media, but one meant for a DVD probably won't fit on a CD

---

