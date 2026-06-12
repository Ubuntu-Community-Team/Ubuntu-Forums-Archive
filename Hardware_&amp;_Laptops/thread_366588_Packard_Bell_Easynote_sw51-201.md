---
title: "Packard Bell Easynote sw51-201"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by Rinias on 2007-02-21
Hello !

So I got a PackardBell Easynote SW51-201 laptop and was rather pleased on the whole with how it works- it doesn't have all the options of other laptops, but it seems to be doing a good job. Here's the specs : [http://www.itplace.be/catalog/product_info-1_15+54456.html](http://www.itplace.be/catalog/product_info-1_15+54456.html) (page not in English but the specs are nonetheless there...)

So I wanted to put the newest (6.10) Ubuntu on it. (Note : Even though the proc is an AMD Turion X2, I would be putting the i386 version on it to have all the goodies ;) ) Normal graphic booting would leave me stuck on the Ubuntu load up screen so I changed some options which eventually let me into the live CD part. (I can't say that I figured out how to do a text install- maybe I did, maybe I didn't... Anyway...) 

I went to fire up the install to disk program which, besides the long wait for the map to zoom in on my city to choose my time zone, went well until I got to the partitioning part. I always set up my partitions myself (I dual boot with XP because I need to keep Mr. Gates around for a couple of programs used at school). The HDD is 120 G which I partitioned into 4 partitions : 2 NTFS partitions (~50 G) a swap partition (~1 G) and the rest for Linux. The problem is that the Ubuntu partitioner loads up and shows me that I have 117 G of free space. *Abort installation*

What I don't understand is that Slackware 10.2 has no problems getting this all set up- in fact I even tried making the Linux partitions in Slack (swap + ext3 for simplicity's sake) and then going back into Ubuntu... I would go ahead and use Slack but I haven't the time to configure and I would like to have the options available in Ubuntu.

So... Could this possibly be an issue with the disk controller or some other driver that is perhaps proprietary ? I don't understand why it won't work. I also tried 6.06 LTS but to no avail... Would a netinstall be more suited to my situation ?

I'd really love to get Ubuntu going on this laptop with as little hacking as possible... Any suggestions ? (Yeah, ok, so I should have picked up the ASUS :s lol)

Thanks so much for your time and suggestions!

Rinias

---

### Post by Rinias on 2007-02-26
Well... I'm glad to say that a new dowload of the i386 image and a "noapic" before the -- on the bootline (as well as unpartitioned, free space on the disk) seems to have done the job :) Back in Linux-land once more ;)

Now if only I can get my school to use Linux-compatible CAD and FEM software... :s

Riri

---

