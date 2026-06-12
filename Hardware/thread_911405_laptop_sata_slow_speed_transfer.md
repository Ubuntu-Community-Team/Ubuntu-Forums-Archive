---
title: "laptop sata slow speed transfer"
date: 2008-09-05
forum: Hardware
---

### Post by wardy277 on 2008-09-05
Hi,

I have a HP DV9700 with 2 sata 5400 HDDs (etx3) running hardy 64bit

I have been noticing slow transfer speeds and jerky playback. Every 15-20 minutes there is a half second skip wth vlc. I wondered if it may be the hdds so i did some testing. I tried copying single 350mb files from one hdd to another and i dont get speeds above 5mbps and no faster when copying on the same drive? same when copying from my external drive to my home dir i dont get faster than 7Mbps

What is gonig on. I have done some research and they are referring to gutsy. This is a new laptop so i havnt tried it with gutsy.

I have run the usual tests but i get the slow speeds using terminal's cp. I have read that satas dont need to use hdparm to tweak them. can anyone help?

---

### Post by tamoneya on 2008-09-05
lets get hard data on individual drives:```
hdparm -t /dev/sda
hdparm -t /dev/sdb
```

---

### Post by wardy277 on 2008-09-06
This is what i get, th anx for the help

/dev/sda:
 Timing buffered disk reads:  184 MB in  3.02 seconds =  60.99 MB/sec
liela@liela:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:  136 MB in  3.00 seconds =  45.30 MB/sec


This is nothing close to what i actually get.

---

