---
title: "Problem reading (supposedly) good Install CDs"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by sumguy231 on 2006-10-07
I just picked up an old barely-adequate PC. The more relevant stats are:
*Cyrix II M-300 266MHz (Pentium II Equivalent)
*48 MB of Ram
*Generic Unkown 24X IDE CD-ROM drive.
*Currently running Windows 98 (Ewwww....)
(I don't plan on running X or anything, I'm trying to do a minimal server install.)

After starting the install, I kept getting read errors from the CD, so I used the 'verify' option after rebooting. It didn't check out fine, and among the verbose errors I saw lots of entries along the lines of 'hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }' 

For the install, I tried two discs, both which gave the same problem. One was an older Kubuntu 6.06.1 Alternate Install disc I had used for a previous install on another machine and the other I had just downloaded (the md5sum checked out ok, and it tested itself fine on another PC.)
In addition, I also tried another drive (I had an old quad speed drive laying around - also IDE.)
I'm stumped and currently just thinking about:
1.) Going for some form of net install or
2.) Trying another distro (I *really* don't want to go for that.)
Any suggestions?

---

### Post by meng on 2006-10-07
With your system, esp. the 48MB RAM, you're going to find it difficult to run Ubuntu I should think. I would venture to say this is not barely-adequate but actually inadequate. You may be better off going for something much more lightweight, perhaps Damn Small Linux or its ilk.

---

### Post by sumguy231 on 2006-10-08
Well, it would seem I have no choice anyway. For some reason, Damn Small won't boot on one drive, but will on the other. It does run surprisingly well, even with X.

---

