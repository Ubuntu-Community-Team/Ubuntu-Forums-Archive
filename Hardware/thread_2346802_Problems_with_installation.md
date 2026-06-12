---
title: "Problems with installation"
date: 2016-12-18
forum: Hardware
---

### Post by durward2 on 2016-12-18
My computer:
motherboard: Asus A7S333
cpu: AMD Athlon XP2200+
RAM: 1280MB (2x512, 1x256) checked: w/o errors
hdd: 80GB WD800JB - checked: w/o errors
optical: CDRW & DVDROM - installation disks check out, w/o errors
video: Matrox Millennium G450 dual head (AGP 4x)- works on all installations that run, mostly from DVD
audio: CMI8738
Network: Kingston KNE111TX - works as some installations have been updated
modem: 56K HCF

All of the Ubuntu and Lubuntu variants I used were 32-bit versions. Most run from the DVD, but will not complete installation, they get about 90% and stop.

Ubuntu 8.04 will install and run; but I cannot down-load any additional programs nor will the browsers work.

All installations of Ubuntu above 8.04 do not seem to work; Lubuntu 14.04 installs and seems to run; however, no Internet browser will load to run; all create run-time errors.
Lubuntu 16.10 32-bit runs from the DVD, but will not complete the installation. I have tried four different AGP video cards, but none work above 1024 x 768. The network card seems to work as I can connect to other computers on my network and I can move files from the other computers to this one. I have 6 desktops and two laptops in this room with only 1 running Windows; the others running Ubuntu 14 to 16; in the other room, I have 4 Macs with OS X 10.6, 10.10, 10.10, and 10.11 AND one Windows 10 and two laptops with Ubuntu 15.10 and 1 with Lubuntu 14.04. So, I have a lot of experience with computers and Ubuntu.

I just cannot get this particular machine going. It belongs to my retired preacher friend (and father in law to my daughter). It had Windows XP sp2. The Internet Explorer would not load but a few web pages. The man is completely computer illiterate.

Durward T. Stockman
retired teacher of computer, math, and physics.

---

### Post by mörgæs on 2016-12-19
This is old hardware and the processor does not have SSE2. 

From a live boot of Lubuntu 16.10 please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags so we can see more about it.

---

### Post by gordintoronto on 2016-12-20
You're talking about a computer which is at least 13 years old. Perhaps some version of Puppy Linux will run on it, but a more modern computer will produce a much happier experience.

Where I live, I can pick up a six-year-old "off-lease" computer for a little over $100, and it will run Xubuntu like gangbusters.

---

### Post by DuckHook on 2016-12-20
> **durward2 said:**
> …The man is completely computer illiterate…On the technical front, you are in good hands with both *mörgæs* and *gordintoronto*, so I won't jump in. My question is more of a "meta" one…

Does your friend really wish to move to Linux? Pardon my sticking my nose into your business, but since you mentioned it, I think it wise to reconsider whether this OS is the best move for him. Most "completely computer illiterate" people find the familiar and the slick far more comforting than the unfamiliar and the geeky. And, despite how much we may love this OS, it has to be admitted that it is both unfamiliar and technical, especially to the uninitiated.

And now that I've given some food for thought, I'll back out of this.

---

