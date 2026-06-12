---
title: "Hard drive"
date: 2010-02-17
forum: Hardware
---

### Post by Zidaps on 2010-02-17
I just bought a Hard Drive off of ebay, its supposed to be 750 Gb. connected it and formatted it (ext3) and mounted it... Its now telling me that the capacity is 698.6 Gb and that 30 Gb are used... But the drive is empty #-o

Anyone know why this is the case? and How can I get the use of the full 750 Gb as stated on the hard drive label??

---

### Post by amac777 on 2010-02-17
750 Gb advertised on box = 698.49 GB in real life  (YES, they lied!)

for proof, see [http://www.epowermac.com.au/shop/pc/viewContent.asp?idpage=28](http://www.epowermac.com.au/shop/pc/viewContent.asp?idpage=28)

Also, the 30 GB used, I believe it's reserve to help prevent fragmentation as files are added to the disk (about 5% of the capacity).

Edit: here's a post (see #3) that explains something about the used space on ext3/ext4: [http://gparted-forum.surf4.info/viewtopic.php?id=13021](http://gparted-forum.surf4.info/viewtopic.php?id=13021)

---

### Post by juan.villa on 2010-02-17
A lot of the difference comes from the fact that the word Giga in the scientific community means 10e9 (or 1000mb). In the computer world we do everything in power of 2, so to us a gigabyte is 1024mb (not 1000mb). 

Hard drive manufacturers use the [1gb = 1000mb] reference, while our computer operating systems (i.e. ubuntu) uses [1gb = 1024mb].

Hope this helps,

---

### Post by Zidaps on 2010-02-17
Thank You. Very helpful information. Much Appreciated.

---

