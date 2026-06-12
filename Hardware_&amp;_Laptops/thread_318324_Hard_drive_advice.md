---
title: "Hard drive advice"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by SVDtiger on 2006-12-13
hi again, 

my old machine (500 p3) will soon need a new hard drive i do believe as tonight the 40gb Western Digital slowed almost to halt but came back on. i have checked power cables and all seem connected tightly. so its either drive or power supply or even the power company i guess. but this drive is old and has seen a long tour

 i am sight challenged, so i dont have much i can spend on my system  even though its about only activity i do have still. i need to find a good deal if at all possible. who do you folks like on the net that has fair or low prices and wont rip me off on a small hard drive
or maybe 2. what brands also please. i really dont need huge drive as i now only do very minor loading. this is a 40gb with 30gb free but if it dies and i not have replacement ill surely be in trouble

 what does the spin speeds have to offer us is something i have always wanted to understand too. im guessing seek time but not sure.


i also thought that if smaller drives were fairly cheap or even still for sale somewhere. i would maybe get 2  and try other distro's for something to do. ill never leave Ubuntu. no worries there :) but i would like to taste some other flavors if i can. 

i cannot express the thanks i have for Ubuntu and how it has helped me  but do know im way beyond grateful. John

---

### Post by Fully216 on 2006-12-13
It is great that you have lots of questions.  Let me try to answer a few.  

The easiest is the drive speed.  This is how fast it spins relating to how fast data can be fetched.  In most cases, IDE drives run around 7200 rpm.  

I would try to get one on newegg if you want to go online ($60 for 160 GB).  Many stores have very reasonable prices, although they tend to carry the bigger, cutting edge type stuff.

Any major band is good.  I use a western digital and a seagate.  Maxtor are also good.

---

### Post by SVDtiger on 2006-12-13
thank you for the guidance. ill go check newegg. have a safe and happy holiday. best regards

---

### Post by zgornel on 2006-12-14
40 GB hard drives are hard to find. The best prices are now for 160-200GB hard drives. You might find that a 40GB costs 10-20$ less than a 160 one :D .

---

### Post by esaym on 2006-12-14
I have had lots of western digitals and maxtors die on me.  I have never had a problem with seagate.  I have also heard that samsung is good.  Newegg is going to be the best prices for new hardware, otherwise you will have to use ebay and buy used stuff but that is iffy.

Try installing smartctl and then do
```
smartctl -a /dev/hda
```
and show us what it spits out :D

---

### Post by SVDtiger on 2006-12-14
i installed the program and ran it but i cant get any drive info? its probably me doing something incorrect

  smartctl -a /dev/hda
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/hda failed: No such file or directory

---

### Post by louistan3 on 2006-12-14
you could try tigerdirect.com.. sometimes they have some good deals there.. or you might also like some refurbished ones.. which they also have.. :)

hope u find a good deal!

---

### Post by esaym on 2006-12-16
> **SVDtiger said:**
> i installed the program and ran it but i cant get any drive info? its probably me doing something incorrect

  smartctl -a /dev/hda
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/hda failed: No such file or directory

hmm perhaps you hard drive is on hdb or hdc?

---

