---
title: "LiteOn DVD+/-RW"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by Im_Just_GrayT on 2006-06-08
I just bought a LiteOn DVD+/-RW  SHW-160P6S10C drive and it seemed to work alright reading disks. I hadnt tried burning anything until after I upgraded to 6.06 LTS. 
  
Just today, I upgraded and I also decided to burn a data DVD. I used k3b to burn it and everything seemed to be going fine until it started writing. It didnt seem to be doing anything, so I just assumed it was really slow(i've never burnt a dvd before) so I left the room and came back a while later. 

A while later It said it was at 1% and had been going for over 30mins. Eventually I just stopped it because I realised at this speed it would take well over 2 full days to burn 1 dvd. And I dont think thats normal.  

Anyway, now I cant even get it to manually mount any disk.
The drive works find under that beast microsoft calls an operating system(winxp) 

Any Ideas as to why this is happening and/or how I can fix it? Any help would be greatly appreciated.

The details of my system configureation:
IDE Primary Master: 60gb Hard disk
IDE Primary Slave: (empty)
IDE Secondary Master: LiteOn DVD+/-RW
IDE Secondary Slave: (cd burner that came with my computer) I believe it is an LG.

Thanks!:D

:EDIT:
After a reboot I can now mount disks just fine, Although I dont expect the speed problem has fixed itself, as I have already tried burning after a reboot with the same problem

---

### Post by ekarni on 2006-06-08
Maybe try burning with another program?  (e.g. GnomeBaker or just search for something else)  DVD's are kinda expensive for coasters, so you might also consider burning a CD first as a preliminary test before moving to DVDs.

As a point of reference, I also have a LiteOn DVD-R/W drive (different model than yours) that works fine under Breezy, and takes ~40 minutes to burn ~4GB to a DVD.

---

### Post by Im_Just_GrayT on 2006-06-09
Do I need to configure scsi emulation to use gnomebaker?  It quits before writing with a cdrecord error. I tried "cdrecord -scanbus" and it just gives a big error about not being able to find /dev/pg*. Just wondering because I've heard that cdrecord only supports scsi. Thanks!

---

### Post by Im_Just_GrayT on 2006-06-09
Nevermind that last message, I found that the problem was my device permissions.
A quick chmod 666 on my burner soved the problem, and thanks for suggesting gnomebaker,
It works great!

---

