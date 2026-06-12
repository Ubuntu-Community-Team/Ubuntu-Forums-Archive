---
title: "Problems with Ubuntu and Windows on two separate hdds"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by watermelancholic on 2009-01-17
hey folks. this is my first time posting here and i'd like to say that these forums have helped immensely for past the year that i've been using ubuntu. i've learned enough about linux to get by, and i really enjoy using it most of the time.

however there are a few things windows xp is superior in(namely compatibility with certain hardware and certain programs), and only so many of my favorite windows programs work well with wine.

now to the issue at hand: i have two hdds, a 320gig and an 80gig. ever since i bought the 320g, i've been trying to have Windows on it, and Ubuntu on the 80g. while i can install them on the hdds fine, after a day or two, things start going wrong. 

corrupted filesystems on both drives(which chkdsk and fsck never completely remedy), overall slower operation, the clocks on OSes get off by 12 hours, etc. etc. eventually it gets to the point where one of the installs(usually the Windows one) is completely unusable except as an external storage drive on Ubuntu.

i've tried again and again, using different windows xp discs, different versions of ubuntu. the two drives are set with the 320 as the master and the 80 as the slave. i don't believe the drives are damaged, or else i don't think they would be able to install OSes and run them in the first place(correct me if i'm wrong, i wouldn't doubt it if i were). i'm obviously missing something and i'll bet it's a simple solution.

any suggestions would be greatly appreciated! let me know if you need my hardware specs, anything's output or log file, anything at all. i'd really like to be able to get my ideal setup up and running for good!

thanks in advance!

---

### Post by TonyFordz on 2009-01-17
Hey there, on a note of wither or not you can install on a damaged HD unfortinatly you can depending on the type of damage the drive has but I have had this type of problem in the past back with version 7 of Ubuntu with Windows XP Pro which I solved with changing my motherboards battery & that only corrected the problems with my clocks being way off as for the corrupt files I dont want to tell you what to do but honestly Hard Drives are pretty damn cheap these days if you shop right online & many you can get free shipping on like my 2 500GB SATA's cost me like $60.00 each brand new OEM & they have worked very well for the past 3 months I have been using them though at first it was a pain in the a** to get Ubuntu to find the hard drives in the boot up window which I finally got around by whipping out the partition on the 2nd one leaving it raw for Ubuntu to format to its own partitions & so on. If you can boot into Ubuntu back everything up thats important get yourself a cheap drive install on it & see if it does the same thing. Also keep in mind that if your installing on two different hard drives that are setup as Master / Slave the Master drive will still be holding the boot information for both so anything that corrupts the Master most likely will also affect the slaves boot information also.

---

