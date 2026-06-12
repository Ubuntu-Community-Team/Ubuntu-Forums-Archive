---
title: "Cheap home server - Hardware suggestions"
date: 2016-04-17
forum: Hardware
---

### Post by Drenriza on 2016-04-17
Hi all

I am in the process of looking for hardware to make a cheap (low powered) home server to run Samba (mirror software raid disks) along with gitlab for my work files.

I am thinking of buying an AMD MB and CPU because AMD is much more friendly to unlock their processor capabilities and handle multiple processes very well.
Which i would like in regards to my software raid and transfer files to and from the system.

But that might not work well with finding low powered hardware, since i want the system to cost (electricity) as little as possible.

Anyone who can suggest some hardware they have had good experience with that works with Ubuntu out of the box?

Thanks on advance
Kind regards

---

### Post by spit4520 on 2016-04-17
Hello,


my suggestion would to go the pentium and or the i3 route. I love AMD and Intel equally and you need to understand their use cases for each processor. The AMD processors are actually better at server like tasks opposed to the non Xeon chips from Intel (from my experience) where as the Intel chips are better at higher work loads and tend to just be faster. That said you can get a AMD chip for very cheap or you could get a cheap intel chip. The lowest power chip that intel sells that is being used in the server style market is the [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157475](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157475) but the prices is something to be debated. I recently built 3 servers for my home to learn from them and try and experiment with them as I am a college student I am unable to fork out large amount of cash in fact I was able to build all 3 with only $300. I bought 2 of the following [http://www.amazon.com/Rosewill-1000Mbps-Gigabit-Express-RC-411v2/dp/B004F34ONC?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o01_s00](http://www.amazon.com/Rosewill-1000Mbps-Gigabit-Express-RC-411v2/dp/B004F34ONC?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o01_s00) for use with connecting a client to two separate machine and I went to a local business and asked if they had any computers that were going to be tossed because of age and or upgrading and I asked if I could buy one I ended up buying two similar to this one [http://www.ebay.com/itm/HP-Compaq-6000-Pro-SFF-Desktop-PC-Intel-Core2-Duo-E8400-3-0GHz-4G-80G-Win-XP-Pro-/170990681003](http://www.ebay.com/itm/HP-Compaq-6000-Pro-SFF-Desktop-PC-Intel-Core2-Duo-E8400-3-0GHz-4G-80G-Win-XP-Pro-/170990681003) Granted I only had the Intel core 2 E6550 chip with 4 gigs of ram. I put a cheap 1TB drive in it and loaded ubuntu basic server and I was off to the races. I also managed to find and i3-4130 on Craig list for $10 and i just bought a cheap mother board and since the price of ddr3 ram is falling through the floor bought some. I got lucky with my parts, but I suggest either spending a little more to get newer hard ware or spending your budget and getting older hardware and just upgrading some piece of it.


I hope that helped.

Please feel free to inbox me with more questions I would be more than happy to help :)

---

### Post by Bucky Ball on 2016-04-17
Have you [seen these]("http://www.hardkernel.com/main/main.php")? A [Raspberry Pi]("http://raspberry.piaustralia.com.au/") may also do the trick although not quite as powerful. (That link is to the Australian site but they're available internationally.)

---

### Post by MartyBuntu on 2016-04-17
My home storage server runs Ubuntu 14.04 and is an AMD AM1 based motherboard with an Athlon 5350 processor. Works great.

---

### Post by him610 on 2016-04-17
Mine was built with a barebones FoxConn a few years ago. It has an Atom CPU, 2 GB RAM, a 1 GB HDD, and boots from freeNas on a USB stick. It is very dependable; the only time I had to restart it was after we had a prolonged power outage. If I was going to do it again, I think I would use a refurbished desktop from Newegg or Amazon.

---

