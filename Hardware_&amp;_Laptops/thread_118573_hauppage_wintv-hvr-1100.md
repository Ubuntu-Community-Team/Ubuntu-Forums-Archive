---
title: "hauppage wintv-hvr-1100"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by endless on 2006-01-17
[http://www.hauppauge.co.uk/pages/products/data_hvr1100.html](http://www.hauppauge.co.uk/pages/products/data_hvr1100.html)

Any idea if I will be able to get this tv tuner card to work in ubuntu? And the DVB-T part? (which would be the reason for me to buy it in the first place)

Thanks!

---

### Post by chasboz on 2006-02-12
Quick answer to that is no for the present. I have tried and failed to get a squeek from this card so far.

Unless you want to experiment with an unauthorsied kernel update breezy badger as it stand right now does not support the chipset found on this card.

Chas

---

### Post by bionicman on 2006-02-12
The Hauppauge HVR 1100/1300  DVB components are identical to the newer Nova-t (90002) card. Use drivers for the   Nova-t & at least you will have DVB!

---

### Post by Spermy on 2007-04-08
I have my Hauppauge HVR1100 working in Ubuntu 6.06

Have a post here somewhere about it, i did need help though! Have also added it to the Hardware compatibility guide.

---

### Post by cblanquer on 2007-05-03
Could you post the link to the former post you mentioned, I am trying to quickly activate my HVR 1300 (at least DVB part).
THX

---

### Post by Spermy on 2007-05-03
[http://ubuntuforums.org/showthread.php?t=394991&highlight=hauppauge+hvr+1100]("http://ubuntuforums.org/showthread.php?t=394991&highlight=hauppauge+hvr+1100")


Have since broken it again, I think installing a ubuntu update killed it as gXine now says "no input plugin" or similar!

Have had a little look at fixing it, but not a good try yet!

---

### Post by cblanquer on 2007-05-04
Finally I could make my hauppauge wintv-hvr-1300 work:
[LIST]
[*]DVB
[*]analog input from satbox (bad image quality)
[/LIST] 
Analog seems not to be working as TvTime coul dnot catch any channel (actually I did not plug any antena to the analog input so it seems a "human error").
I followed [http://ubuntuforums.org/showthread.php?t=337960&highlight=hauppauge+1300](http://ubuntuforums.org/showthread.php?t=337960&highlight=hauppauge+1300) to install the DVB drivers.

The bad thing is that it broke my webcam setup  and /dev/video0 seems unavailable.
I followed my own post regarding updating the webcam driver readapting it for Feisty Fawn, but no success:
[http://ubuntuforums.org/showthread.php?p=2009418#poststop](http://ubuntuforums.org/showthread.php?p=2009418#poststop)

From other posts, it seems the last version has something wrong. 

UPDATE 20070505
I tryed reinstalling webcam drivers, then the DVB driver does not work anymore. It seems they fight each other to getting control over /dev/video0 device, regardless of what actual H/W is underneath.
I am thinking about doing the following:
1. take out the webcam, 
2. reinstall DVB drivers, 
3. plug back in the webcam and 
4. reinstall the webcam drivers, 

unless anybody has a better idea... Always welcome, I am feeling to be reinventing the weel, at least I had to be doing similar things under 6.10.

---

### Post by LazyTownRocks on 2007-05-11
where are the Ubuntu nova-t drivers anyone? Thanx.

---

