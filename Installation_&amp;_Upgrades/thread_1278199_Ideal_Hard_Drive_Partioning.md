---
title: "Ideal Hard Drive Partioning"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by afhkhan on 2009-09-29
Hi All,

Greetings for a good day! I am new to Ubuntu and was wondering what will be the ideal way of formatting my 80 GB hard disk on my laptop. I am installing Ubuntu desktop 9.04 and want to know how much of space is recommended for each mount point. I will be running only one instance of Ubuntu and **_NO dual boot_**. Any advice is greatly appreciated and I would request little detailed info as it will help for my next installation as well!

---

### Post by star3am on 2009-09-29
Hallo :) and welcome to Ubuntu (clap)

I use Ubuntu on my laptop too, I opted to use the "Alternate install CD"
as with that I am able to encrypt my partitions, I opted to use the full disc default layout, encrypted, that way if anyone snatches my lappy, my data is safe. 

I also use a USB external HDD, 160G ... for that I setup an encrypted partition 60G ext3 and a 100G NTFS partition, you have many, many options, 

All the best, I hope you have a smooth ride, 

ciao/Riaan:popcorn:

---

### Post by pmlxuser on 2009-09-29
15 Gb for /
4GB for swap
60 for /home

all data will be in home , system files in / viola

---

### Post by afhkhan on 2009-09-29
> **pmlxuser said:**
> 15 Gb for /
4GB for swap
60 for /home

all data will be in home , system files in / viola

Many Thanks! Do I keep the swap at the start or end?

---

### Post by afhkhan on 2009-09-29
> **star3am said:**
> Hallo :) and welcome to Ubuntu (clap)

I use Ubuntu on my laptop too, I opted to use the "Alternate install CD"
as with that I am able to encrypt my partitions, I opted to use the full disc default layout, encrypted, that way if anyone snatches my lappy, my data is safe. 

I also use a USB external HDD, 160G ... for that I setup an encrypted partition 60G ext3 and a 100G NTFS partition, you have many, many options, 

All the best, I hope you have a smooth ride, 

ciao/Riaan:popcorn:

Many Thanks for your reply! Since I am a starter, I would like to go by basics!

---

### Post by pmlxuser on 2009-09-29
doesn't really matter but the best is to keep it at the start coz when doing a reinstallation the / and swap are usualy are reformatted and I like keeping such close to each other. but as said befoer it doesn't really matter.

---

