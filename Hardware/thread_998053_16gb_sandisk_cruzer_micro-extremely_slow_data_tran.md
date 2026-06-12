---
title: "16gb sandisk cruzer micro-extremely slow data transfer rates"
date: 2008-11-30
forum: Hardware
---

### Post by motoperpetuo on 2008-11-30
i just picked up a 16gb sandisk cruzer micro flash drive the other day and finally got around to beginning to transfer data to it today. the trouble is that it's extremely slow. i'm trying to copy about 1gb of data (consisting of over 6000 files, mostly small). so far, it's been copying for about fifteen minutes and the system indicates that it has 41 minutes to go. judging from how slow it's transferring data, i'm guessing that it will be more like two hours.

when i first noticed how slow the transfer rate is, i canceled the transfer, took out the 4gb sandisk cruzer micro i was using until i got the new 16gb flash drive, and connected it to the same USB port. i was able to copy my 1gb of data to the 4gb flash drive in about five minutes.

for what it's worth, both flash drives are formatted to NTFS.

is it normal for a larger flash drive like my new 16gb drive to be a lot slower than a smaller drive, or is my 16gb drive just a lemon?

---

### Post by davidshere on 2009-01-16
Mine does something similar --

I'm on an extremely fast server right now trying to copy CD isos onto my 16 GB cruzer micro.  The first 300-400 MB is done in two or three seconds.  Then the last 100-200 MB takes about 30 more seconds.  It continues to slow... then it says "598.2 of 598.2 MB copied ... 0 seconds left" for about two minutes.  Then the dialogue finally goes away.

I can only assume that the data is transferred with no errors.

I recommend zipping the files you want to transfer into 100-200 MB zip files, and transferring the zips one by one.  PITA, but might be the only thing that works.  When I try to transfer two CD ISOs at the same time, it hangs after about 60% of the transfer.  When I do them one at a time, it at least gets to 100% before hanging.

I transferred a torrent of about 120 songs onto it at home... only to realize that when I got to work only about 40 of them were actually on it.  It must have frozen/crashed... I wasn't watching... and I assumed it was transferred completely.

I also have a 4GB with which I have no problems.  It's been through the wash twice... still no problems.

---

### Post by Lutherian on 2009-05-13
This is a fault with the Flash Drive itself.
Many good people have been suckered - myself included.
Story goes like this... your 8GB Sandisk cruzer get lost/broken/full/old ,
it performed so well that you naturally purchase another... but his time you go for the 16GB - MISTAKE 
I should've stuck with the 8GB ... running portable apps on it... forget about it :(

---

### Post by Lutherian on 2009-05-13
This is a fault with the Flash Drive itself.
Many good people have been suckered - myself included.
Story goes like this... your 8GB Sandisk cruzer get lost/broken/full/old ,
it performed so well that you naturally purchase another... but his time you go for the 16GB - MISTAKE 
I should've stuck with the 8GB ... running portable apps on it... forget about it :(

---

### Post by davidshere on 2009-05-14
> **Lutherian said:**
> This is a fault with the Flash Drive itself.
It works fine with Windows.

---

### Post by ahumin on 2009-05-31
i had the same problem with a brand new 8GB cruzer. on my first transfer of several files, it sped through the first 580MB or so, and then slowed to a crawl for the remaining 6GB.

my guess is that it appeared fast at first as ubuntu filled up a write buffer, then the drive's true colours shone through because the buffer was filled much faster than the bytes could actually be written to the drive.

i'm returning mine, it says hi-speed transfer on the packet. :mad:

---

### Post by ahumin on 2009-06-04
thought i'd do a bit more troubleshooting before returning it. tried it on a pc running vista and it was consistently fast with a transfer totalling 7GB. [removed the U3 partition]("http://kb.sandisk.com/cgi-bin/sandisk_en.cfg/php/enduser/std_adp.php?p_faqid=2550&p_created=1232580910&p_sid=N2Qjwvzj&p_brand=&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTIwLDEyMCZwX3Byb2RzPTAmcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXJlbW92ZSB1Mw**&p_li=&p_topview=1") and reformatted it to ntfs, when i tested it on my ubuntu pc again it was slower (but not by much).

i can't tell if it's the drive or if it's *nix OSes having trouble communicating with it (seems osx users have similar issues with cruzer micro drives).

the weirdest thing is the inverse relationship of transfer size to speed. if i do a 1GB transfer the speed is ~4MB/s if i do 7GB it slows down to ~1MB/s. on the vista pc it was steady rate > 10MB/s. read is good enough in ubuntu, i got 35MB/s "copying" a file from it to /dev/null

don't know how i'm going to convince store to give me refund when it'll work fine on their windoze machines :(

update: used dd to wipe the drive before returning it and it got 5.2M/s. :roll:

---

### Post by Cadeyrn on 2011-06-20
You think that's bad? My 16GB Cruzer also freezes up my system when I try to transfer files, and I just deduced that if I have VLC watch a movie off of it for more than half an hour, that freezes my system too. Not only is my Cruzer useless, but it makes me have to do a hard restart. SanDisk lost a loyal customer today. After the last two Cruzers I've gotten being epic fails, I'm never getting a flash drive from those guys AGAIN.

---

