---
title: "Hardware RAID"
date: 2011-11-02
forum: Hardware
---

### Post by lile001 on 2011-11-02
I am looking for someone with experience with Hardware RAID on Ubuntu.  

I am not very skilled at any of this stuff, but am determined to build my next machine with hardware RAID.  Why?  1.  I had a complete, flameout failure attempt at installing Fakeraid, and finally gave up, after several weeks of frustrating effort.  2.  I imagine that hardware RAID should be closer to plug-and-play.  3. I run a business and need my computer to be very reliable.  

Like I say my Linux skillz are pretty lame, however I have successfully installed or configured a few things and think that I could probably have some success, with a few hints.  I've been messing around with Linux just a couple of years. 

I am looking at this board:
[SIZE=2][/SIZE]**[SIZE=2][B]3Ware 9650SE-2LP-SGL, Half-Length, Low Profile, Internal SATA II  Hardware RAID Controller Cardm, PCI Express x1, 2 port w/ 3Gb/sec, RAID  0, 1, JBOD and Single Disk- Single**[/SIZE][/B]

only because I found a review of it where "some guy" said he successfully installed it on Linux.  I don't really have any idea if that is a good choice or not.  Any experiences?  This board costs $170 or so, you can find them from $39 to $2000.  Figuring you get what you pay for, I have shied away fromt he cheapest boards, but other than that I am just guessing what might be a good choice.  

I'd sure like to hear from someone who had successfully installed hardware RAID under Ubuntu.

---

### Post by lile001 on 2011-11-02
Well, here is one off the hardware compatibility thread that doesn't work:

[INDENT]OS = Ubuntu 11.04 
CPU = Intel Core i7 970 12 core
Motherboard = Asus R.O.G. Rampage III Formula
Graphics = Asus HD 6950 2GB
Memory = 24GB  (6 x Corsair 4 GB, DDR3-2000)
Primary Drive = Corsair 128GB SSD SATA-3
Hardware RAID = RocketRAID 2320
RAID array = 2TB RAID 10 (4 x WD 1TB, SATA-II)
PSU = Cooler Master Silent Pro Gold Series 1000 PSU
Tower = Cooler Master HAF Tower

Everything works except for the hardware raid array. This works in Windows 7 but not in 11.04.
[/INDENT]

---

### Post by lile001 on 2011-11-02
Here is some hopeful news:  

[INDENT]I just set up a new workstation for home use. It uses usb wifi and a hardware raid 1. The netgear wg111v2 works with no modification just install and reboot and it comes up. **The raid card is an Areca arc-1200,** again it comes up with no problem and is transparent to Lucid Lynx.

 The workstation is home made with a Gigabyte motherboard and Seagate es drives.

I recommend both of these items.[/INDENT]

---

### Post by lile001 on 2011-11-02
> **lile001 said:**
> Here is some hopeful news:  
[INDENT]I just set up a new workstation for home use. It uses usb wifi and a hardware raid 1. The netgear wg111v2 works with no modification just install and reboot and it comes up. **The raid card is an Areca arc-1200,** again it comes up with no problem and is transparent to Lucid Lynx.

 The workstation is home made with a Gigabyte motherboard and Seagate es drives.

I recommend both of these items.[/INDENT]

Uh oh, first reveiw I found for this Areca card is really a flamer:

[INDENT]
[LIST=1]
[*]      Useless For RAID1    
       By Pro Tech  - Dec 2, 2009  -  Full review provided by  [IMG]http://www.gstatic.com/productsearch/static/merchant_logo/newegg.com_fav.png[/IMG]  [Newegg.com]("http://www.google.com/url?q=http://www.newegg.com/Product/ProductReview.aspx%3FItem%3D16-151-031%26campaigncode%3DOTC-GoogleReview&usg=AFQjCNFxTwvFmYRMz4C_rR_44vZEq5CYAg&ei=D0axTpHUL5O2NpOr1NoI&ved=0CA8Qow0")  
      Pros: Fast RAID1 performance. Good installation documentation.Cons:  Completely lacks any error handling or recovery documentation either in  the manual or online. Useless "knowledge base", worthless support by  email only. Completely unreliable data recovery and poorly designed  screens leave you in the dark.I  bought this as a RAID1 boot drive but it will soon be tossed in my junk  box. I set it up as RAID1 with 2 new WD "Black" 500GB HDs for easy  recovery if a drive should a drive fail. With each boot I check my RAID  arrays for error messages - none until one day it would not boot. I look  through the error logs (the only way to know) showed a drive failure on  channel 2. No problem I replaced the drive with a brand new drive and  gave it time (12 hours) to rebuild - nope didn't happen. It just sat  there.Now a normal RAID1 card will  at least let you boot on the good drive while it rebuilds - not this  one. It will not load it's BIOS unless everything is perfect. I  eventually gave up and deleted the volume and rebuilt the array, and  manually loaded the OS and all my application. You buy a RAID1 set so  that all you have to d is swap a drive and the card does the rest -  since none of that worked and no under the hood documentation exists I  give it 1 star only because zero is not a option.          Was this review helpful?    Yes - No  
  
[/LIST]
[/INDENT]

---

### Post by lile001 on 2011-11-02
Here is another bad review of Areca:

[INDENT]    ARECA Support Is Terrible    
       By MidNightTechie  - Feb 19, 2009  -  [Newegg.com]("http://www.google.com/url?q=http://www.newegg.com/Product/ProductReview.aspx%3FItem%3D16-131-003%26campaigncode%3DOTC-GoogleReview&usg=AFQjCNESRIC3l5Z7a9bZvCjJKdASif9ndg&ei=1UexTqrcKIimNpiomdsI&ved=0CE0Qow0")  
      Pros: Lots of Lucky Stellar ReviewsCons:  It is HIGHLY recommended that you discontinue the 'ARECA Controller  Cards'. Tech Ram USA has the support contract for ARECA Cards. I went  thru 4 Asians before I got one I could understand and I spent 5 years in  & out of Thailand, Taiwan, Japan and Hong Kong. After sending an  email below to Areca.com.tw/support/, TekRam called and suggested that I  try the PCI 8X card in a PCI 4X slot vice the PCIe 8X...Any computer  tech knows that the slots are incompatible in slot alignment and  distance from the backplane mounting plate. WILL NOT SWAP. 3-Ware RAID  Controller Cards are well supported & better quality! If carried,  will have to compete with Tiger on prices!!Installed  "Areca ARC-1210 PCI-Express x8 SATA II Controller Card" in the 2nd PCIe  8X slot of MSI P6N SLI Platium motherboard with lastest BIOS v1.70 for  RAID-0 with 4 "Hitachi Deskstar 1 Tbyte SATA harddrives plugged into  this SATA RAID card and 4 TBytes in external RAID-1 3-Ware SideCar.  Tried 5 times on two different identical computer systems! Will not load  McRAID BIOS to control RAID drives hooked up to the card. Will replace  with 3-Ware RAID card.  [/INDENT]

---

### Post by lile001 on 2011-11-02
3WARE turns up zeros hits on the Hardware Compatibility thread.  Although that last guy recommends it, it sounds untried.

---

