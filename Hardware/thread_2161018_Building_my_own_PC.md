---
title: "Building my own PC"
date: 2013-07-09
forum: Hardware
---

### Post by sark89 on 2013-07-09
Hi all,
I'm new to this forum so sorry if this is in the wrong section. I'm looking at building my own computer, I've got a parts list:
[TABLE]
[TR]
[TH="align: left"]Type[/TH]
[TH="align: left"]Item[/TH]
[TH="align: left"]Price[/TH]
[/TR]
[TR]
[TD="align: left"]**CPU**[/TD]
[TD="align: left"][Intel Core i5-4430 3.0GHz Quad-Core Processor]("http://uk.pcpartpicker.com/part/intel-cpu-bx80646i54430")[/TD]
[TD="align: left"]£146.39 @ Aria PC[/TD]
[/TR]
[TR]
[TD="align: left"]**CPU Cooler**[/TD]
[TD="align: left"][Corsair H60 74.4 CFM Liquid CPU Cooler]("http://uk.pcpartpicker.com/part/corsair-cpu-cooler-cwch60")[/TD]
[TD="align: left"]£60.72 @ Scan.co.uk[/TD]
[/TR]
[TR]
[TD="align: left"]**Motherboard**[/TD]
[TD="align: left"][Asus H87I-PLUS Mini ITX LGA1150 Motherboard]("http://uk.pcpartpicker.com/part/asus-motherboard-h87iplus")[/TD]
[TD="align: left"]£90.29 @ Dabs[/TD]
[/TR]
[TR]
[TD="align: left"]**Memory**[/TD]
[TD="align: left"][Corsair Vengeance 8GB (2 x 4GB) DDR3-1600 Memory]("http://uk.pcpartpicker.com/part/corsair-memory-cml8gx3m2a1600c9b")[/TD]
[TD="align: left"]£55.00 @ Ebuyer[/TD]
[/TR]
[TR]
[TD="align: left"]**Storage**[/TD]
[TD="align: left"][Samsung 840 Series 120GB 2.5" Solid State Disk]("http://uk.pcpartpicker.com/part/samsung-internal-hard-drive-mz7td120kw")[/TD]
[TD="align: left"]£89.99 @ Amazon UK[/TD]
[/TR]
[TR]
[TD="align: left"]**Video Card**[/TD]
[TD="align: left"][EVGA GeForce GTX 650 Ti Boost 1GB Video Card]("http://uk.pcpartpicker.com/part/evga-video-card-01gp43656kr")[/TD]
[TD="align: left"]£129.18 @ Scan.co.uk[/TD]
[/TR]
[TR]
[TD="align: left"]**Case**[/TD]
[TD="align: left"][BitFenix Prodigy (Black) Mini ITX Tower Case]("http://uk.pcpartpicker.com/part/bitfenix-case-bfcpro300kkxskrp")[/TD]
[TD="align: left"]£64.34 @ Amazon UK[/TD]
[/TR]
[TR]
[TD="align: left"]**Power Supply**[/TD]
[TD="align: left"][Corsair Builder 600W ATX12V Power Supply]("http://uk.pcpartpicker.com/part/corsair-power-supply-cmpsu600cx")[/TD]
[/TR]
[/TABLE]

Now, I want to install both windows 7 and ubuntu onto the SSD to dual boot into either windows or ubuntu. Will I be smacked in the face with no end of trouble with ubuntu and hardware issues? I've installed ubuntu on a few computers mainly my old macbook and it worked fine apart from the mouse track pad refused to work smoothly which was a real shame. Thanks in advance!

---

### Post by Grafens on 2013-07-09
You only need liquid cooling if your going to overclock the cpu otherwise its a waste. As for duel booting first install windows then ubuntu. You need to watch out for UEFI but as your building the thing yourself it should be ok, check the mainboard specs anyway just to be sure. You need to know if UEFI is installed whether it can be turned off through the BIOS

---

### Post by kurt18947 on 2013-07-09
> **Grafens said:**
> You only need liquid cooling if your going to overclock the cpu otherwise its a waste. As for duel booting first install windows then ubuntu. You need to watch out for UEFI but as your building the thing yourself it should be ok, check the mainboard specs anyway just to be sure. You need to know if UEFI is installed whether it can be turned off through the BIOS

Yes, check on file systems supported.  I'm not sure if the biggest problem with installing linux/Ubuntu is UEFI or Secure Boot.  I thought Secure Boot was only on assembled machines with Windows 8 installed but I could be wrong.  If I understand it correctly, UEFI would be kinda handy on multi-boot systems assuming it was implemented properly in the system's BIOS/firmware.  As I understand it, UEFI has no issues with 4 partition limitations for one thing and has boot management built in.  Of course the devil is in the details and UEFI & Secure Boot are both pretty new.

---

### Post by maglax on 2013-07-09
[SIZE=2][FONT=courier new]I just build a pc (with windows 7 and an i5 processor) (No linux allowed on it unfortunately) here a few tips:[/FONT]
[FONT=courier new]1. I would also get a hdd to work alongside your  sdd. The reason being you only have a 120gb sdd I have pretty much filled up 500gb hdd (I have 19gb left) on a laptop in 9 month.[/FONT]
[FONT=courier new]2. If you have the money and are wanting more memory I would look at this motherboard: ASUS P8Z77-V LK LGA  this will allow for up to 32 gb of ram (newer version of mine)[/FONT]
[FONT=courier new]3. Make 100% sure you do not need more than 600 watts.[/FONT]
[FONT=courier new]4. Grafens is right you most likely will not need liquid cooling I am just using the stock fan.

[/FONT][/SIZE]

---

### Post by Yellow Pasque on 2013-07-09
> **maglax said:**
> If you have the money and are wanting more memory I would look at this motherboard: ASUS P8Z77-V LK LGA  this will allow for up to 32 GB
8GB is more than enough unless the OP is doing something special (lots of VM's, large GIMP images, etc.)

> . Make 100% sure you do not need more than 600 watts.
Nah, a 400W-450W PSU is good enough for a system like that. Most people greatly overestimate power consumption because of all the web sites geared towards gaming, power-hungry video cards (GTX 650Ti boost is not bad in that regard), and OC'ing.

All that said, I would rather spend more money/attention on the GPU (get a GTX660) for a balanced system. You could downgrade to 4GB RAM or cut out the CPU cooler (stock heatsink will be enough unless you're OC'ing, though it won't be the most quiet)

---

