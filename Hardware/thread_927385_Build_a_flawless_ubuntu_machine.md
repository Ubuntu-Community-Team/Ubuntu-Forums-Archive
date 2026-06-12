---
title: "Build a flawless ubuntu machine?"
date: 2008-09-22
forum: Hardware
---

### Post by angelsneverdie on 2008-09-22
Hello all,

I want to build a new desktop - and I want absolutely no problems with unsupported hardware or only marginally supported hardware.  What hardware do the developers use?  I saw the sticky threads about working and non working hardware, but to a novice builder like me it is a bit confusing.

I'm interested in people's advice on the whole deal - from power supply to motherboard to graphics, audio, and hard drives.

But don't worry, it isn't that easy.  I'm also on a budget - there's no way I could spend anything over 1k.  I don't do gaming but need to easily be able to utilize the advance desktop effects.  Mostly i do word processing and web browsing, including videos.

Thanks for any help or advice!

-Mitchell

---

### Post by travm on 2008-09-22
I am no dev, but i would recommend a new ati or nvidia integrated mobo, based on a 780G or 8200 chipset (ati or Nv respectively).  I am currently using a gigabyte ma78gm-s2h, and aside from some initial video driver problems, (which were more because of my TV being connected via HDMI than anything else) just worked out of the box.  

Probably your biggest hurdles will be setting up your machine to work with videos, its not hard.  Just completely different from how you do it on a windoze box.

Regardless, you should use google and search every piece of hardware (your case and psu are exempt) with the word linux beside it to see if anything comes up.  Wireless and video are probably the biggest problem areas.  Also some newer soundblaster chips don't work unless things have changed recently.(and they do change often quickly).

---

### Post by yosepht on 2008-09-23
I just put together a new system about 3 weeks ago and I am
thrilled on how everything worked out. I am not sure if it
can be done with that $ restriction but here is the parts list-
Asus P5Q Deluxe,4gig corsair ddr2, Nvidia 8800GT,320gig SATA 
hd,samsung DVD writer,thermaltake 700w power supply and case.
Try pricing this with 2gig of ram,smaller PS,a less pricier
video card. I think you can get close to your budget. I have
Ubuntu 8.04 running on mine I am very happy with it.

---

### Post by tydfil on 2008-10-07
For anyone coming to this thread late.  The 8200 mobos are not a good choice at the moment as they are one the few nvidia chipsets which are not supported.  You will have to select Low Graphics Mode every boot as the hardware is not detected.  Install the nvidia-glx and you get unstable deaktop.

Hardy and Intrepid seem to have probs with these boards.  Maybe they will solve it beofe final release of Intrepid.

---

### Post by cariboo on 2008-10-07
I would suggest staying away from asus until they get their bios sorted out. If you check in the forums there seem to be a lot more problems with asus motherboards then with any other manufacturer. Now this is either because they sell a lot of motherboards, or that there is a problem with them. 

I have have always had good luck with Nvidia based MSI motherboards, even though MSI doesn't want to have anything to do with Linux, they just seem to work right out of the box. I have usedthe same motherboard for the lst three releases and never had a problem with any thing. Video and audio just work and I have a mix of ide, sata and esata drives that always get detected in the right order.

Jim

---

### Post by yt_l9 on 2009-01-21
Here is what I just built over the summer/fall:

MoBo = $110 (80 after rebate)
Foxconn P45A-S
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813186148](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186148) 

CPU = $282 (can oviously substitute with a less expensive model)
Intel Q9550
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115041](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115041)

GPU = $120
Zotac 8800GT
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500006](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500006)

RAM = $2x43
2x (pqi DDR2 800 4Gb)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820141366](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141366)

OD = $26
Samsung 22x DVD burner
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827151171](http://www.newegg.com/Product/Product.aspx?Item=N82E16827151171)

HDD = $ 70
Samsung 750Gb 7200rpm
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152100](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152100)

Case + Power Supply = $65
HEC tower + 585W PS
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811121073](http://www.newegg.com/Product/Product.aspx?Item=N82E16811121073)


Which comes to about $750

I had to get some assorted adapters and I opted for a card reader, a cpu fan and other assorted items and landed right around the $1k mark.  I'm very pleased with my machine and have had absolutely no problems with 8.10

I also run virtualbox with XP and 7 beta on seperate desktops.  This system is plenty powerfull for anything I'm doing including ripping/encoding/compiling.

Hope this helps!

---

