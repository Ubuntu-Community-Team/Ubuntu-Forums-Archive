---
title: "Building a new build machine, problems?"
date: 2010-08-19
forum: Hardware
---

### Post by rbhkamal on 2010-08-19
Below are the specs of the new 64bit build system my company will be ordering, Do you have anything to say/suggest/criticize? 

I will be installing 64bit Ubuntu Linux with a sh$t load of virtual machines running on it.


Motherboard ($700):
GIGABYTE GA-X58A-UD9 LGA 1366 Intel X58 SATA 6Gb/s USB 3.0 XL ATX Intel Motherboard
	[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128446](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128446)

CPU ($990):
Intel Core i7-980X Extreme Edition 3.33GHz LGA 1366 130W Six-Core Desktop Processor
	[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115223](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115223)

Memory ($165):
CORSAIR XMS3 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model TR3X6G1600C8 G 
	[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145236](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145236)

Graphics ($345):
SAPPHIRE TOXIC 100282TXSR Radeon HD 5850 1GB 256-bit GDDR5 PCI Express 2.0 x16
	[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102881](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102881)

Storage ( 4 x $75):
Western Digital Caviar Black WD6401AALS 640GB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5"
Western Digital Caviar Black WD6401AALS 640GB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5"
Western Digital Caviar Black WD6401AALS 640GB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5"
Western Digital Caviar Black WD6401AALS 640GB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5"
	[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136319](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136319)

Power Supply ($300):
CORSAIR Professional Series AX1200 1200W ATX12V v2.31 / EPS12V v2.92
	[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139014)

Case ($200):
COOLER MASTER HAF X RC-942-KKN1 Black Steel/ Plastic ATX Full Tower Computer Case 
	[http://www.newegg.com/Product/Product.aspx?Item=N82E16811119225](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119225)



Total Cost: $3000

---

### Post by cascade9 on 2010-08-20
Just my take on this setup....

1200watts is far more than you would need for that sytem. 

A 59850 is a good gamers card, but for VM use, pointless. 

6GB, getting 9GB or 12GB would be a better idea for VM use.  

The GA-X58A-UD9 offers virtually nothing over the cheaper models, just more PCIe slots. Its a huge chunk of money to spend to just get 4way SLI/crossfire. The GA-X58A-UD7 does 3way SLI/crossfire, which is still more than any sane person would want, and its half the cost......

Intel XXXXXX-'extreme' CPUs are always a rippoff. You could get 12 cores of opteron goodness, or a really nice Phenom II X6 + motherboard + 8GB DDR3 for less than just the 980X CPU.

---

### Post by rbhkamal on 2010-08-20
I agree... but I have about 3500 budget and I want to make the best out of it. 

Now... back to the hunt for the perfect build machine. any suggestions are appreciated just remember the 3.5K budget!

---

### Post by cascade9 on 2010-08-21
Just because you have a $3.5K budget doesnt mean you have to spend it all...you could cut your costs by %50 and wouldnt really notice the difference. 

But if you want to spend it all, then you can. ;) 

What is your intended use aside from virtual machines? Gaming, media playback, data stoage, torrent box, all of teh above? 

AMD hater or not? (seriously, a 12core opteron is about the same, even a bit less than the i980, motheroboards less than the GA-X58A-UD9, and you would get quad-channel RAM. Its well within budget, but if you dislike AMD I wont put the parts up)

---

### Post by rbhkamal on 2010-08-21
I like AMD more than Intel and the system is for compiling code on the host os and on virtual machines (up to 3 compiles at one time)

Think compiling kernel :) ... awaiting ur specs

---

### Post by TimEnid on 2010-08-21
did you read the reviews on that motherboard?

---

### Post by cascade9 on 2010-08-23
> **rbhkamal said:**
> I like AMD more than Intel and the system is for compiling code on the host os and on virtual machines (up to 3 compiles at one time)

Think compiling kernel :) ... awaiting ur specs

Compling, damn. Its one area I've never got any decent data on.....I'm not sure if it 'likes' more cores or more MHz. If it likes more cores, the opteron would be faster, if it likes MHz, then the 980X would be faster.

---

### Post by rbhkamal on 2010-08-24
The total cost with the UPS is now $2700, what do you think?

APC Smart-UPS 1500VA LCD 120V 
    [http://www.apc.com/resource/include/techspec_index.cfm?base_sku=SMT1500](http://www.apc.com/resource/include/techspec_index.cfm?base_sku=SMT1500)

Media Reader: 
  PLEXTOR 24X DVD/CD Writer Black SATA Model PX-880SA-26 LightScribe Support 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16827249051](http://www.newegg.com/Product/Product.aspx?Item=N82E16827249051)

Computer Case: 
  COOLER MASTER HAF X RC-942-KKN1 Black Steel/ Plastic ATX Full Tower Computer Case 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16811119225](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119225)

Storage (4 harddrives) in RAID5: 
  Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive 
  Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive 
  Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive 
  Western Digital Caviar Black WD1002FAEX 1TB 7200 RPM SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136533](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136533)

Motherboard:
  ASUS Crosshair IV Formula AM3 AMD 890FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131644](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131644)

Video Card:
  EVGA 512-P3-N871-AR GeForce 9800 GTX+ 512MB 256-bit DDR3 PCI Express 2.0 x16 HDCP Ready SLI Support Video Card 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130339](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130339)

Power Supply:
  CORSAIR CMPSU-850TX 850W ATX12V 2.2 / EPS12V 2.91 SLI Ready CrossFire Ready Active PFC Power Supply 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16817139009](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139009)

Memory:
  G.SKILL Ripjaws Series 16GB (4 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model F3-12800CL9Q-16GBRL 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231315](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231315)

Processor:
  AMD Phenom II X6 1090T Black Edition Thuban 3.2GHz Socket AM3 125W Six-Core Desktop Processor HDT90ZFBGRBOX 
    [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103849](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103849)

---

### Post by bobpur on 2010-08-24
Why not blow the rest on a couple 10,000 rpm raptors and a couple of large capacity (2 tbs) 7200 rpm drives for Storage. RAID the raptors. If you're going to build a crazy go fast computer, don't scrimp on the hard drives. :)

I just looked over your hdd specs one more time. I missed the RAID 5 part (JBOD?). I've never fooled around with that. 

Really, whatever works, but I'd think about the raptors and a RAID 0 (STRIPE) for a boost in speed.

---

### Post by rbhkamal on 2010-08-25
RAID5 is not JBOD... lol (I had to Google that). It's basically RAID0 with fault-tolerance ability. So I would be able to get some nice numbers out of it!

Anyway, on bootup I will be creating an 8+GB ramdisk which will be used for I/O intensive tasks. On shutdown/reboot the contents will be saved to the raid.

---

### Post by Yellow Pasque on 2010-08-25
Any reason for the 9800GTX instead of a GTX 460 1GB?

> **bobpur said:**
> Why not blow the rest on a couple 10,000 rpm raptors and a couple of large capacity (2 tbs) 7200 rpm drives for Storage. RAID the raptors.
Meh, might as well get an SSD for the root system if going that route.

---

