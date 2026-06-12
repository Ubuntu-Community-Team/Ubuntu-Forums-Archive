---
title: "srO: CDROM (ioctl) error"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by MonkSS on 2009-04-01
hi!
Ubuntu is a new thing for me....
And i can use some help :D
I wanna instal hem to a no sistem hardware.
Is a live cd.
well i boot the CD, and i have the instalation option, i select the language then the instal, and then i get this error

" srO CDROM (ioctl) error,command: Get configuration 46 00 00 00 00 00 00 00 20 00
[610.554554] (<- this numbers are difret on evry line)Buffer I/O error on device sr0, logical block 1
[xxx.xxxxxx] Buffer I/O error on device sr0, logical block x
[xxx.xxxxxx] Buffer I/O error on device sr0, logical block x
[xxx.xxxxxx] Buffer I/O error on device sr0, logical block x
[xxx.xxxxxx] Buffer I/O error on device sr0, logical block x


And this never stops...

I dont really know what to do.
Hope u can healp me.
Thank you , and i`m sorry for my eanglish.

---

### Post by dandnsmith on 2009-04-01
Typically, I see this sort of error when booting a liveCD on the non-quiet mode, but it is usually limited, and the boot completes.

I'd try things like:
- swapping for a new CD drive
- writing a new CD on different hardware
- performing an extensive memtest to give confidence in the RAM

---

### Post by jsanguin on 2009-04-15
I've got the same problem, and after trying with several machines I can come to the conclusion that somehow the CD/DVD drive has a hard time reading the disk (even when you just burned in that machine). What worked for me was to take that CD into a robust desktop (even and old Compaq Presario will do) and then see if it passes the CD test provided in the Ubuntu Installation Menu. If this machine has no problems reading the disk, make a copy using Nero (or whatever you have there). Then use the copy in your Linux target machine. This worked for me, hope it helps.

---

