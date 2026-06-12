---
title: "can anyone help me get DVD Decrypter"
date: 2008-08-09
forum: General Help
---

### Post by Exile666 on 2008-08-09
I used to use DVD Decrypter because of the fact it can simply extract the .vob files, when i had vista install. But in Ubuntu i can seem to find anything just as easy. Anyway, when i run 'DVD....' under wine it doesn't seem to find my dvd drive. this is what i get in the log.

-Initialising SPTI...
-Searching for SCSI / ATAPI devices...
-No devices detected!

can anyone help? or direct me to a program that does the same thing.

---

### Post by mb_webguy on 2008-08-09
What do you use DVD Decrypter for?  There are quite a few very good Linux applications for working with DVDs...

---

### Post by sendblink23 on 2008-08-09
> **mb_webguy said:**
> What do you use DVD Decrypter for?  There are quite a few very good Linux applications for working with DVDs...

he needs it TO BURN encrypted DVDs ;)  Rip them

---

### Post by Cope57 on 2008-08-09
[**Ubuntu Linux DVD Shrink, DVD Decrypter Guide**]("http://mrbass.org/linux/ubuntu/dvdshrink/")


You could also try one of these... Look for them in your repositories.

**gopchop**
[INDENT]*Fast, lossless cuts-only editor for MPEG2 video files*

gopchop cuts and merges MPEG2 video streams. gopchop uses a method to cut streams that does not require re-encoding, and therefore is fast and not prone to the artifacts and degradation of quality inherent in re-encoding.
However, cuts are limited to I-frames or group-of-picture (GOP) boundaries. These frames occur frequently enough, and often times at scene transitions, so that gopchop's method is adequate for many applications.

The typical use is manually editing commercials out of recorded television programs.

Another application is splitting .VOB files from dual-layer DVD rips so that the content can be re-authored such that each half will fit on one
single-layer DVD recordable.[/INDENT]


**vobcopy**
[INDENT]*A tool to copy DVD VOBs to hard disk*

vobcopy copies DVD .vob files to harddisk and merges them into file(s) with the name extracted from the DVD. It checks for enough free space on the destination drive and compares the copied size to the size on DVD (in case something went wrong during the copying).

You can also mirror the DVD movie content and copy single files you specify.[/INDENT]

---

### Post by stinger30au on 2008-08-09
grab the free edition of dvdfab hddecrypter

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

runs fine in wine

save the data to the hdd. then fireup something like dvd9to5 or similar and compress from dvd9 to dvd 5 and burn to dvd with k3b.

a little long winded but it works for free

---

### Post by mc4man on 2008-08-09
> Initialising SPTI...
-Searching for SCSI / ATAPI devices...
-No devices detected!

Open winecfg and see if your drive(s) are shown under the drives tab if not use autodetect.
Try setting Os to windows nt4.0

---

### Post by Exile666 on 2008-08-10
yeah thanks mc4man, doing what you said worked.

---

