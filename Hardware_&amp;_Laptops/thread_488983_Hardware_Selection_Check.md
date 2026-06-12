---
title: "Hardware Selection Check"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by damber on 2007-06-30
Hi,

I'm building a new system and want to make sure that everything will work properly under ubuntu feisty.   My current selection of hardware is (partially) listed below.  Please can you have a quick look and let me know if you see any potential problems.  

**_Motherboard_**
one of these:
Abit AW9D MAX with PCI-E WIFI Bundle Socket 775 7.1 Channel Audio Crossfire ready ATX 	
Asus STRIKER EXTREME 680I SLI Socket 775 onboard Audio ATX
[I]I'm hoping to use the onboard RAID controller of these boards for one of the disk arrays - not much info on whether these are supported or not.. any ideas ?
I don't care about the wifi, I have a wifi bridge that plugs into the ethernet port, so not an issue[/I]

**_Graphics_**
2x Innovision 3D 8800GTS 320MB GDDR3 DVI PCI-E Graphics Card 
[I]I will be using a tri-head/monitor setup, using 2 outputs from 1 card, and one from the other for 3x 19" flat panels - as used previously with both Fedora 6 and ubuntu feisty.
I see that some people have had issues with the 8800 gtx and even the 8800 gts with feisty - is this a common issue, or is it isolated/now fixed/etc ? - what alternative do you recommend of equivalent price/performance[/I]

**_Storage disks_**
Storage: 2x Seagate ST3500630AS 500GB Hard Drive SATAII 16MB Cache 7200RPM - OEM
System: 2x WD Raptor WD740DFD 74GB SATA 10KRPM 16MB Cache - OEM

**_Raid Controller_**
Adaptec RAID 1220SA - storage controller (RAID) - SATA-300 - PCI Express x1
*For the other disk array *

**_Processor & Memory:_**
Corsair 4GB Kit (4x1GB) DDR2 800MHz/PC2-6400 XMS2 Memory Non-ECC Unbuffered
Intel Core 2 Quad Q6600 (2.4GHz 1066MHz) Socket 775 L2 8MB Cache (2x4MB (4MB per core pair))

I'm thinking that the main concerns are:
- Graphics cards... as always, but at least they're nVidia, instead of ATi's...!
- Onboard Audio (I have a pci based audio card (creative audigy) I can use instead, so no real issue)
- Onboard Raid (I could add two raid controller cards instead of 1+onboard, but would prefer not to, as it makes things more complicated_
- RAID controller - adaptec seem to be reasonably supported, but I've not found specific confirmation of this card)
- Quad Core Processor - I don't expect this to prevent it from working... but how well will the OS take advantage of it ?

So.. what do you think ?  Will this get me into endless hours of fretting over dumbass drivers / hardware incompatibility, or will I get a good working system out of it ?  

Thanks in advance,

---

### Post by damber on 2007-07-01
any thoughts anyone ?

---

### Post by RichJacot on 2007-07-17
Please let me know how you make out with the build you have listed.  

I was just reading the specs and reviews on the Asus STRIKER EXTREME and just searched this forum to see if any one was using it with Ubuntu.  I'm wanting to build a rig like your describing before the end of the year.  The biggest reason I'm wanting to wait is to see what AMD's quad core release does to Intel's quad prices.

---

### Post by damber on 2007-07-17
In the end I read too many bad reviews of the Striker Extreme -  a fair few people had problems with the bios (affecting both windows and linux) which took some fiddling and an upgrade to resolve, plus reported instabilities and I was less keen to use the nvidia chipset than the intel one etc.. so instead I went with the ASUS P5WDG2-WS ([http://www.asus.com/products4.aspx?l1=3&l2=11&l3=248&model=1289&modelmenu=1](http://www.asus.com/products4.aspx?l1=3&l2=11&l3=248&model=1289&modelmenu=1))

my final setup is as follows:

[LIST]
[*][CoolerMaster CMSTACKER 831 case]("http://www.ebuyer.com/UK/product/129035")
[*][CoolerMaster RealPower Pro 850W PSU]("http://www.ebuyer.com/UK/product/126776")

[*][ASUS P5WDG2-WS Pro Motherboard]("http://www.dabs.com/productview.aspx?Quicklinx=478Z&CategorySelectedId=11143&PageMode=1&NavigationKey=11143,50626,379730000")
[*][Intel Q6600 Quad Core Processor 1066Mhz FSB - 2.4Ghz + 8 MB Cache]("http://www.ebuyer.com/UK/product/124869")
[*][4GB Corsair DDR2 800MHz/PC2-6400 XMS2 Memory]("http://www.ebuyer.com/UK/product/111439")
[*][2x nvidia 8800 GTS 320MB Graphics Cards (from Innovision)]("http://www.ebuyer.com/UK/product/125114")

[*][AMCC 3way 9500S 4 Port SATA RAID Controller]("http://www.ebuyer.com/UK/product/85440")
[*][2x WD Raptor WD740DFD 74GB SATA 10KRPM 16MB Cache]("http://www.ebuyer.com/UK/product/114117")
[*][2x WD WD5000ABYS 500GB RAID Enhanced Hard Drive SATA II 7200RPM 16MB Cache]("http://www.ebuyer.com/UK/product/129398")

[*][Ubuntu Feisty Fawn/7.04 64bit OS]("http://www.ubuntu.com/")
[/LIST]

It runs like a charm now, but I did have some issues getting the graphics cards to work.  Basically the OS/driver/whatever wasn't allocating enough memory address space for both cards to work/be initialised at the same time, so you need to increase this in the 32bit version of the OS using the kernel parameter vmalloc=256M (or whatever the value is to fix it - start at 128 and increment ) - the /usr/share/doc/NVIDIA*/README.txt document describes this in detail - search for "vmalloc" for more info.  This doesn't/shouldn't happen in the 64bit version due to the greater memory addressing space. I simply upgraded to Ubuntu 64 bit and it resolved the issue immediately.

Couple of things:
[LIST=1]
[*]The 8800GTS cards are huge.. I mean really big - they take up 2 slots EACH (so make sure your PCI-E slots are not directly next to each other, and take this into account when thinking of adding other cards in there) - and they are as long as the ATX board is wide - so be careful of space in your case, as some cases would make the installation of these and the HDD's extremely challenging, and quite thermally problematic.
[*]The 3way raid controller was a great buy - I actually got it off ebay for £95 and it really has saved me a lot of headaches with my drives... turn it on, do some (really simple) config and then it "just works" - if you're going to get a raid controller, get a 3way or other REAL hardware controller - many of the cards (most I found) rely on os and bios drivers to make them work, and many will cause you problems in linux - some wont, but even those that work in, say, debian, may not work in feisty's install process.. a friend has this problem at the moment.
[*]The case is also quite big - but with the cards being so big, it's a good idea to keep your case choice of a similar size so it's not too cramped.
[*]The graphics cards run really hot (despite their onboard fan/cooling) - make sure you have a 'windy' case 
[*]The HDD drive cage only holds 4x3.5" drives - if you want more, you can use the 5.25" space (there's plenty of it - x6 slots), but you'll need to buy extra housing.
[*]I used my old IDE DVD-RW, and used the only IDE connection on the board... I would strongly suggest getting an SATA based cd/dvd drive  - I'll be replacing mine shortly.
[*]The PCI-E slots, although both PCI-Ex16 slots, don't run at x16 at the same time if 2 cards are installed - it downgrades one to x8.  This seems to be common across boards using the intel 975 chipset, so if you want full power on both, you may want to search around some more and pay a little extra - or wait a while.  For me the compromise was ok.
[/LIST]
Other than that - don't be afraid of the newer nvidia cards  despite some threads hanging around saying that they don't work yet - other than the memory allocation issue I had (because I was using 2 cards), there have been no issues with them.

Hope that's useful to someone who's looking for linux compatible hardware of this nature.

---

