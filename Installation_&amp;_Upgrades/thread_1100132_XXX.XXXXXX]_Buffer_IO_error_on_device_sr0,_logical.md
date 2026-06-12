---
title: "XXX.XXXXXX] Buffer I/O error on device sr0, logical block XXXXXX"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by Zampfeo on 2009-03-18
[IMG]http://img21.imageshack.us/img21/3871/fgbfdgwow.jpg[/IMG]

I get this loop anytime I try to use an Ubuntu function, boot from live cd, install, memory check, check for errors, wubi installation, wubi SPCE(This is not what it said at all, just a guess) bypass installation, wubi boot from cd, etc. etc.

I've tried all of the above and taking out all my HDDs (3 S ATA drives) and changing my IDE cd drive to slave and master.

I only have one single IDE cd on one IDE ribbion cable and 3 S ATA HDDs all on a Gigabyte Ga EP35 DSL3 mobo.

---

### Post by cariboo on 2009-03-19
I have the same problem when I burn CD's to fast. I usually burn image files at 4X.

Jim

---

### Post by jtu on 2009-03-21
I've had this same problem with alternate CD's for both 8.04 and 8.10. I've burned about 6 coasters on 3 different machines at varying speeds. The CD's don't even pass the integrity check. It's always the same sector number.

I've seen many other postings with the same problem, but no solutions.

HELP!

---

### Post by terry31415 on 2009-03-23
have you tried changing the ide master/slave/cable select settings with the drive on both cable connections. My setup would only work in one configuration and to change settings if I removed the cd rom.
Good luck.

---

### Post by klopus on 2009-03-30
Since it's WUBI no real CD/DVD drives are involved. It's just squashfs image files on Visa hard drive which has no bad blocks. Reinstalling WUBI doesn't help at all. The sr0 error always references 2 same blocks. I even made sure that new WUBI install allocates different HD NTFS blocks for images. Still same error and same 2 blocks! That's extremely annoying since it significantly prolongs boot time for the installed Ubuntu. Any ideas?

---

