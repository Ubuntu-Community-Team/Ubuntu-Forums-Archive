---
title: "Hardware help for cheap NAS"
date: 2008-07-22
forum: Hardware
---

### Post by chrisclarke on 2008-07-22
[COLOR="Red"]*UPDATE: New proposed hardware configuration and prices below.*[/COLOR]

Thanks for taking the time to read my humble thread!

As most people who look for backup solutions, I had a catastrophic failure losing some pretty important stuff and now I want to prevent it.  I'm building a home NAS with a µ budget **[COLOR="Red"]$530.68[/COLOR] ($0.415/GB)**.

I've organized this in lists to make it easier to read, thoughts and questions first with my details to follow.  I also tacked on my installation strategy at the end for those interested.  Please let me know if you have comments, suggestions, or words of encouragement!

**Thoughts and Questions**
[LIST]
[*]Intel Atom, Atom boards appear to be limited to 2x SATA which is a problem
[*]miniITX, seems expensive, few boards with 4+ SATA or 1Gb NIC and compatibility worrisome
[*]other chipsets, the graphics on my motherboard are WAY overpowered anyone know of any other chipsets or motherboards I may be missing
[*]AMD, I'd like to keep it Intel because the board, CPU, chipset, and NIC are all single source plus I didn't see much cost benefit of AMD
[/LIST]

**Qualifiers**
[LIST]
[*]evaluated FreeNAS and similar, like them but it's no fun, this is as much a learning experience as a useful device, plus I want ext3
[*]looking to build and configure myself, I know some NAS devices exist that are cheaper but again, learning experience
[/LIST]

**Goals**
[LIST]
[*]1+ TB with dual redundancy (similar to mirroring in RAID 1 but at the system level, more on this in Strategy)
[*]Google whitebox strategy, multiple cheap disposable systems
[*]fast w/ 1Gb NIC
[*]100% Linux compatible system without tweaking (for example, my motherboard choice was based on Intel NIC as I have read of problems with Realtek)
[*]single network volume to facilitate easier backup and use
[*]easily repeatable setup
[*]learn more about Ubuntu and **_WRITE A CONCISE AND COMPLETE GUIDE_** to give back to community
[/LIST]

**Strategy**
[LIST]
[*]initially 1 whitebox w/ 3 drives in RAID 5 storage configuration, handles single drive failure (weak, within single system)
[*]future 3 whiteboxes (in 2+ locations) w/ 4 drives in RAID 5 storage configuration with 100% replication, triple redundancy (strong, multiple systems and redundancy)
[*]single whitebox accessible to network users, self replication handled by whiteboxes (once more than one exist)
[/LIST]

**Whitebox**
[LIST]
[*]separate OS and storage volumes
[*]software RAID because excess processing power available, lower cost, and personal experience with bad RAID card
[*]low power requirement and heat generation
[*]spare processing power for future tasks and/or SETI contributions
[*]read only boot drives, run system out of RAM after boot and dual redundancy boot drives
[*]must be whitebox, in other words *cheap*
[/LIST]

**System**
click on product name for links to Newegg or Monoprice
[LIST][*]*Newegg*
[*][COLOR="RoyalBlue"]motherboard[/COLOR] [Intel G35 microATX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121337") [COLOR="Red"]$89.99 [/COLOR] (1Gb Intel NIC, 4x SATA, LGA 775 up to 1333MHz FSB so upgradable)
[*][COLOR="RoyalBlue"]processor[/COLOR] [Intel Celeron 430 Conroe-L 1.8GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116039") [COLOR="Red"]$39.99[/COLOR]
[*][COLOR="RoyalBlue"]RAM[/COLOR] [OCZ (2x 1GB) DDR2 800 (PC2 6400)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227139") [COLOR="Red"]$19.49[/COLOR]
[*][COLOR="RoyalBlue"]OS drives[/COLOR] [2x OCZ RALLY 4GB USB flash drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227145") [COLOR="Red"]$25.98[/COLOR]  ($12.99 each)
[*][COLOR="RoyalBlue"]case[/COLOR] [APEX TX-381 microATX Mid Tower 300W]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811154071") [COLOR="Red"]$49.99[/COLOR]
[*][COLOR="RoyalBlue"]case fan (protect HDD)[/COLOR] [Scythe 120mm]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835185004") [COLOR="Red"]$12.99[/COLOR]
[*][COLOR="RoyalBlue"]Storage HDD[/COLOR] [ 3x Western Digital Caviar 640GB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136218") [COLOR="Red"]$254.97[/COLOR] ($84.99 each)
[*]*Monoprice*
[*][COLOR="RoyalBlue"]internal USB connectors (for OS drives)[/COLOR] [2-Outlet USB Plate]("http://www.monoprice.com/products/product.asp?c_id=103&cp_id=10307&cs_id=1030701&p_id=2210&seq=1&format=2") [COLOR="Red"]$1.62[/COLOR]
[*][COLOR="RoyalBlue"]internal SATA cables[/COLOR] [4x SATA cables]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10226&cs_id=1022601&p_id=3399&seq=1&format=2") [COLOR="Red"]$2.96[/COLOR] ($0.74 each)
[*][COLOR="RoyalBlue"]SATA power splitter[/COLOR] [2x SATA power splitter]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10226&cs_id=1022604&p_id=2195&seq=1&format=2") [COLOR="Red"]$2.46[/COLOR] ($1.23 each)
[*]**[COLOR="RoyalBlue"]TOTAL[/COLOR] [COLOR="Red"]$530.68[/COLOR] ($0.415/GB)**
[/LIST]


**Installation**
when I start install in September, I will start new thread post in appropriate forum and link it here
[LIST]
[*]Ubuntu Server 8.04
[*]install OS to 4GB flash drives in RAID 1
[*]add storage HDD in RAID 5
[*]setup services, SSH, Samba, rsync, etc.
[*]set OS drives to read only (use AUFS)
[/LIST]

---

### Post by chrisclarke on 2008-07-30
For anyone that is interested in something similar to what I am doing I have found quite a few other resources throughout the net.  I'm a bit disappointed at the lack of feedback here on the Ubuntu forum but this is after all more hardware related.  :-)

This user on the AVS forum, who has done some impressive work in the past, is working on a low cost solution as well.  He and the other users in the thread have a lot of knowledge and experience so I'd recommend checking it out if you are just getting in to it like myself.

[http://www.avsforum.com/avs-vb/showthread.php?t=1045086](http://www.avsforum.com/avs-vb/showthread.php?t=1045086)

---

### Post by sit-ubu-sit on 2008-08-05
I'm trying to do the same thing that you are trying to do.  Unfortunately, I am not as knowledgeable as you are.

I got the idea initially from this link: [http://www.tomsguide.com/us/cheap-fast-diy-raid-5-nas,review-779.html](http://www.tomsguide.com/us/cheap-fast-diy-raid-5-nas,review-779.html)

I'm trying to create a wired NAS that will support 16 hard drives in a CoolerMaster RX 810 chassis.  I have no idea what motherboard, CPU, or memory to get.  I do have a 450W power supply, but have never built my own computer, and don't even know what cable to get to hook up all of the drives.

Also, I have no idea how to configure Ubuntu to allow my Macs to access the files over the network.

I just recently posted in this forum before I found this thread.  So far, I have not received any suggestions on the hardware side.  Of course, it's only been an hour, so perhaps by tomorrow someone will have responded.

---

### Post by tamoneya on 2008-08-05
Two things for you to think about:
1.  It would be cheaper to do 3x500GB in a RAID 5 than 2x 1TB in a RAID0.  You still get the redundancy but more like $240 total.  You could actually do 4x500GB in RAID 10 for less than 2x1TB.  RAID 10 would actually be better performance wise.

2.  $100 for a mATX board is a little much if all you are doing is making a NAS and need just 3 satas (or 4 or 5 satas if you follow item 1)

I personally like gigabyte and if you want 4 satas I would use this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128078](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128078)
if however you go RAID 10 you will need 5 satas and might want this board: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128354](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128354)

---

### Post by chrisclarke on 2008-08-06
> **sit-ubu-sit said:**
> I got the idea initially from this link: [http://www.tomsguide.com/us/cheap-fast-diy-raid-5-nas,review-779.html](http://www.tomsguide.com/us/cheap-fast-diy-raid-5-nas,review-779.html)

Be careful of that link you posted, it is a bit old so some of the advice is no longer true, like about not being able to recover a software raid easily.  It is a good overview though.

> **sit-ubu-sit said:**
> I'm trying to create a wired NAS that will support 16 hard drives in a CoolerMaster RX 810 chassis.  I have no idea what motherboard, CPU, or memory to get.  I do have a 450W power supply, but have never built my own computer, and don't even know what cable to get to hook up all of the drives.

You might consider going with a server type chassis because you have so many drives.  Norco has a new one that has made a lot of people happy on some of the other forums I read.  Check it out, [$325.39 at Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811219021&Tpk=norco%2b4020") including shipping.

As for the other components, you want to focus on low cost but more importantly compatibility.  Make sure key components of the motherboard especially are compatible with your OS.  Realtek Gb LAN cards have been a little problematic with Ubuntu so that's why I went with a more expensive board that has an Intel Gb LAN.

Also, check out that link I have in the second post.  The project odditory is working on for his cheap backup might be right up your alley.  The thread is pretty long but [here is one of the key posts about his cheap backup]("http://www.avsforum.com/avs-vb/showthread.php?p=14373895#post14373895").

> **sit-ubu-sit said:**
> Also, I have no idea how to configure Ubuntu to allow my Macs to access the files over the network.

Samba is probably your best bet to set up the networks share as it works with the major OS's easily.  It's straight forward to setup in Ubuntu and if you put Samba in the search box you'll get a bunch of articles.  [Here is a pretty good one]("http://ubuntuforums.org/showthread.php?t=874163").

---

### Post by chrisclarke on 2008-08-06
> **tamoneya said:**
> 1.  It would be cheaper to do 3x500GB in a RAID 5 than 2x 1TB in a RAID0.  You still get the redundancy but more like $240 total.  You could actually do 4x500GB in RAID 10 for less than 2x1TB.  RAID 10 would actually be better performance wise.

Yeah, that's definitely something I was considering.  I was looking at the WD 640GB drives because they are two platters like the 500GB but have the best $/GB of any drive out there.  The TB drives were attractive because of the nice round number for sizing but I really only have 500GB of data anyway and it's not growing very fast.  Performance isn't too much of an issue because it's over the network, 125MB/s max, and it's just a backup anyway.

> **tamoneya said:**
> 2.  $100 for a mATX board is a little much if all you are doing is making a NAS and need just 3 satas (or 4 or 5 satas if you follow item 1)

I personally like gigabyte and if you want 4 satas I would use this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128078](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128078)
if however you go RAID 10 you will need 5 satas and might want this board: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128354](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128354)

I did check out the other manufacturers boards but I was turned off by what I read about the Realtek GB NIC on most of their boards.  The NIC is pretty important for a NAS so I wanted to avoid having to make any special changes in Ubuntu to get it to function properly.

But good news, Newegg now sells a version of the Intel motherboard I'm looking at as an [OEM part for $5 cheaper]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121337"). :-)

---

