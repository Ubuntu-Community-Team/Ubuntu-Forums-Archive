---
title: "CD/DVD i/o error 5"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by -TK- on 2008-12-07
Hello! 

i was running MS WinXP for about 4 years or so not much problem. Tried Ubuntu when Ubuntu 5.10 released, got some errors so back to XP.

Right now i'm running on Ubuntu 5.04 Live CD. (yeah, yeah it's more than 3 and half years old. i burned it without even check MD5. LOL) running for more than a month already. :'( waited for 8.10 to upgrade.

my pc is a old one. mainboard MS-6718; CPU: Intel PIII 800EB 800 Mhz; chipset Inntel 810; onboard vga; 256 Mb RAM; Samsung ATA hdd 40Gb (less than 3 and half years old, SMART data seem fine.); Samsung CD drive (new, less than 6 month old)

i have a official Ubuntu 8.10 install cd just arrived which i ordered about month ago.

when looked at it, it had a spot on it, so i clean up, seem clean, more than the ubuntu 5.04 live cd i'm using right now.

First, i ran it without CD integrity check first.
i ran Install ubuntu (no live), with full disk partition option. run well until about 23% of copying file. A i/o error 5 appeared, it was about i/o error 5 of (cd image; cd drive or HDD error. suggest clean up cd image; clean up cd drive lens or place the PC at more cool environment.)

i pressed the [OK] it started to live mode.

i restarted the pc, cpu heat was at 46*C

then i did a CD integrity check. no error found. WTH????

i ran install again. this time with manual partition, first 10gb for (/) next 29Gb for (/home) the rest 400Mb for swap. (the full disk option set a over 700 Mb partition as swap)

it ran to 23% of copying files then the same i/o error 5 appeared again. (Ok.... WTH? CD integrity check said no error...)

it started to live mode. i restarted the pc again.

then did a CD integrity again. this time it said 1 error reading file. (Ok... now it it got error...) i pressed a key, it restarted, did CD integrity check again, same 1 error reading file. (hrm.)

i reformat the hdd, set up a 400 Mb partition at the end for swap by other Live CD just for this purport. 

i took out the CD, put the Ubuntu 5.04 Live CD in, start. it went all the way nice. i changed something, install FF2. (5.04 went with FF 1.04), run well after more than 2 day alway on (before tried install 8.10 i was let the Ubuntu 5.04 Live CD run over 4 days without shutdown. 

I tried install Ubuntu 8.10 again. (today morning)

This time i did CD integrity first. 0 error files. (Ok, so no error heh.) did CD integrity again, still 0 error files. (hrm...)

I ran install. go manual partition, BAAM, the i/o error 5 CD/DVD error again at 23% of copying files. (wth?)

i ran install again, no CD integrity check this time, manual partition. the partition data say about both (/) and (/home) used about more than 600 Mb. i checked the format check box.

the install running again. i went way to do some thing else, came back, it was up to 48% of copying files (heh) so i went way again, did something esle, then came back, 68% of copying files. (hrm) went way again... came back... that i/o error 5 pop up again. this time it was at 68% of copying files. (wth?) i pressed [OK] it started to live mode.

I restarted the PC, CPU heat is low. no more than 46*C (when i started running install it was 40*C)

I did CD integrity check. BAAM; 8 error reading files. (WTH?) did CD integrity again, again 8 error.

I took out the CD, put 5.04 live CD in, the live CD run fine, leaved it running then i took a nap (more than 3 hours), the 5.04 live CD still run.

I restarted it, put the Install Ubuntu 8.10 cd in, do a CD integrity check. 1 error reading files this time. (cr@p) took CD out.

(The partition program recognized my hdd as SCSI1(hd0) ... should it be ATA1(hd0)? since i plugged the hdd at first IDE channel as Master, the CD drive as Master at Second IDE channel.)

I put the 5.04 Live cd in, started, and after hours, i reg in here, post this.

WTH happened? Any idea for me? :?

(sorry if my english went bad at some point.) :)

---

### Post by -TK- on 2008-12-08
No suggestion? [img]http://ubuntuforums.org/images/icons/icon9.gif[/img]

---

### Post by MarineMan215 on 2009-04-27
My first post....

Anyway, i know it's been a while but can anyone help us? I've been suffering from the same problem as well (i've only tried 8.10). For some random reason though the installation works if another OS is installed first (so i install my old Windows 98FE, then i install linux, not within windows BTW, and it works...


Thanks in advance,
~MarineMan215

---

