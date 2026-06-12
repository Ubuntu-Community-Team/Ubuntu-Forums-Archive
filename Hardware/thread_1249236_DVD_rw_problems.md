---
title: "DVD rw problems"
date: 2009-08-25
forum: Hardware
---

### Post by ZMB on 2009-08-25
I am having trouble with my two ide dvd-rw drives. I installed 9.04 recently and soon found that my DvD drives are showing the strangest of behaviors. When I put in a dvd movie it will load the disk and bring up the data TS folder. I can not play the dvd in movie player, or vlc and yes I have all of the needed packages installed. The only time a dvd will load is if had been burnt with an iso, it seems (dvd-rw discs are a no go). Data disks are seen by the system but are not mounted as there is reported no media in drive. I am sure my drives work as I have installed ubuntu a couple of times with them. I am sure it is not a motherboard issue as I have swapped my board out with another. I have poured over my bios but I find nothing. I can boot into window and both drives function as they should. I would love some help or feedback.

---

### Post by stinger30au on 2009-08-25
i wouldnt happen to be anything simple like the dvds are both set to cable select by any chance instead of one set to master the other set to slave

the one furtherest away from mobo is master one closest to mobo is slave on the data cable

out of interest, what if u try with 8.04 instead does it make any difference?

---

### Post by ZMB on 2009-08-25
I do not run CS on any of my drives. I have tried 8.04 as well and it still does the same exact thing. Things were working fine in the 7.?? distro. I may just go and get a sata dvd-rw and see what happens....could it be the kernal perhaps?

---

### Post by stinger30au on 2009-08-30
do you have both ide dvd drives plugged in and running at the same time?

what if you run only one as a master, what happens?

what if you swap them round and run the second that was a slave as a master on its own, hen what happens?

---

### Post by ZMB on 2009-09-01
Ok...Things are looking to be a bit wonky as far as the way ubuntu decides to set up my dvdrw drive....I got it work a bit better by running /usr/share/doc/libdvdread4/install-css.sh...It will now play movies, it still has issues reading data cds and burning cd's as well.

---

