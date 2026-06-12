---
title: "Primary NAS but...."
date: 2013-01-07
forum: Hardware
---

### Post by ejkeebler on 2013-01-07
I'm wanting to build my own mini-itx nas, but i'd like it to do a few other things besides storage like stream home videos 1080p, ftp server, store music, pictures, etc. Wondering on suggestions for a mini itx board and cpu?  I don't want to go overboard, but at the same time, if I want to stream some 1080p home video within the intrAnet I don't want it choking.

Considered 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131841&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-NA-_-NA&gclid=CNfF1avv1rQCFQLd4AodgyEAyg](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131841&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-NA-_-NA&gclid=CNfF1avv1rQCFQLd4AodgyEAyg)

and 

[http://www.amazon.com/Intel-G530-CACHE-Processor-BX80623G530/dp/B005LTU54Q](http://www.amazon.com/Intel-G530-CACHE-Processor-BX80623G530/dp/B005LTU54Q)

or maybe [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157247](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157247)

or maybe [http://www.amazon.com/gp/offer-listing/B007S9PF92/](http://www.amazon.com/gp/offer-listing/B007S9PF92/)

any suggestions?  I'd really like to stick with mini-itx and do have 4 hdd i'd like to use, potentially a small ssd (64gb) for an os drive.

---

### Post by Juzz on 2013-01-08
If it's only going to be serving as a server and not being the one to play the media on tv/anywhere - then might I suggest:

[This supermicro board]("http://www.supermicro.nl/products/motherboard/ATOM/X9/X9SBAA-F.cfm")

Or this:
[With 6 ports of sata, so you can use an ssd for os]("http://www.supermicro.nl/products/motherboard/ATOM/ICH9/X7SPA-HF-D525.cfm")

What's cool is that it has IPMI - that's basically a way of remote controlling it over the network ;)

Then if you get 4 big hdd's then you can set them up in software raid 10 (two striped disks that mirror each other).

Supermicro are a company dedicated to producing server and workstation products - so stability should be very high.

Cheers
Juzz

---

### Post by ejkeebler on 2013-01-08
interesting board choice, wish it had 1 more sata connector so i could use 4 storage drives and 1 ssd boot drive...it does include ECC Ram support which is nice since I want to use ZFS, going to have to give strong consideration to this....I wonder how well it will handle streaming 1080p i'll have to check into it, thanks for the suggestion!

---

### Post by Juzz on 2013-01-09
Yes, I have long been considering a replacement for my old server - and I have been considering the 6 port sata board.
One of the things I did was to look at sites that compared cpu power - and my old dual athlon mp appears to be a little slower than the Atom in the 6 port board.

---

### Post by mastablasta on 2013-01-09
what about HP micro server?
 
btw why would you need SSD for OS? and so big at that....i mean you plan to run server on it, right? headless?

---

