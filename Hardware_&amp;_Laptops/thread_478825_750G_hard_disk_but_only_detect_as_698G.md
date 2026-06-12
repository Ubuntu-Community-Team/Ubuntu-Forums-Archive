---
title: "750G hard disk but only detect as 698G?"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by stock99 on 2007-06-19
HI,

  I just brought an seagate 750G hard disk but under ubuntu 7.04 Gparted program , it only pick up 698.64G.   Is there anywhere i can find back my missing 50G disk space?



ps: my kernel is   2.6.20-15-generic #2 SMP

---

### Post by tgm4883 on 2007-06-19
Hmm, that does seem like a little much.  You should be seeing around 715GB on fresh store bought 750GB drive.

---

### Post by stock99 on 2007-06-19
ok, i read somewhere it is the 5% reserve thing that took up the space... and ya, i would expect to get at least 710G.   

I know there is a command line options to specify reserve %   (using mke2fs )     -m reserved-blocks-percentage
.  But to what size is it save to shrink?  I am only going to use this drive for create backup tar file.  Besides, is there a way to do it on gparted ?

---

### Post by srt4play on 2007-06-19
If it's only going to be used for backups, I'd set the reserved blocks percentage to 0.

---

### Post by tgm4883 on 2007-06-19
> **stock99 said:**
> ok, i read somewhere it is the 5% reserve thing that took up the space... and ya, i would expect to get at least 710G.   

I know there is a command line options to specify reserve %   (using mke2fs )     -m reserved-blocks-percentage
.  But to what size is it save to shrink?  I am only going to use this drive for create backup tar file.  Besides, is there a way to do it on gparted ?

Hmm, if the reserve block is 5%, then you should be seeing around 680GB.  Unless the reserve block is less than 5% of total disk space

---

### Post by hardyn on 2007-06-19
698 is right.

2^30 = 1073741824

1000.. / 1073... =0.93 * 750 = 698... all good.

---

