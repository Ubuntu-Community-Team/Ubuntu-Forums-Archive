---
title: "New computer compatability"
date: 2010-10-06
forum: Hardware
---

### Post by Sam3280 on 2010-10-06
Hi,
Just looking for some general advice about linux friendly companies for the hardware for my new computer. Any suggestions appreciated. Thank you 

So far the brands im putting into the computer are:
Thermaltake
Intel
Gigabyte Techologies
Kingston
Western Digital
Samsung

Product details:
Case: Thermaltake V3 Black Edition Mid Tower Case With 450W PSU
[http://tinyurl.com/28tqyxf](http://tinyurl.com/28tqyxf)

CPU: Intel Core i3 530, 2.93GHz, Dual Core, Socket LGA1156, 73W TDP, 2x256KB L2 Cache, 4MB L3 Cache, Intel HD Graphics 733MHz, Boxed, Clarkdale 
[http://tinyurl.com/27ko8yj](http://tinyurl.com/27ko8yj)

Motherboard: Gigabyte GA-G41MT-D3, LGA775, Dual DDR3-1066, Intel G41+ICH7, Onboard GMA X4500, VGA, 4x SATA, 1x IDE, 1x FDD, 1x PCIe x16, 1x PCIe x1, 2x PCI, 8x USB, Gigabit LAN, 7.1ch ALC888B, Micro ATX
[http://tinyurl.com/28pvywe](http://tinyurl.com/28pvywe)

RAM: Kingston 2GB PC3-8500 (1066MHz) DDR3 ECC CL7 DIMM 
[http://tinyurl.com/28p4kca](http://tinyurl.com/28p4kca)

HDD: Western Digital Caviar Green - Hard drive - 1 TB - internal - 3.5" - SATA-300 - buffer: 64 MB
[http://tinyurl.com/255nzm6](http://tinyurl.com/255nzm6)

Optcal Drive: Samsung SH-S223C Internal 22x Speed SATA Dual Layer DVD-Rewritable, DVD±RW Drive 12x, DVD-RAM 16x, +R DL 12x-R DL, Black 
[http://tinyurl.com/22mvybc](http://tinyurl.com/22mvybc)

---

### Post by mastablasta on 2010-10-06
> **Sam3280 said:**
>  Intel HD Graphics 733MHz, 
 are oyu plannign to use Intel built in graphics card? you might have a look into this, because i dont' htink they have a very good support. some do have it while for some support is poor.

---

### Post by Sam3280 on 2010-10-06
I was hoping to be able to use the built in graphics yes

---

### Post by cascade9 on 2010-10-06
Power supplies/cases arent friendly, or unfriendly. The only issue you can get with power supplies is not enough power. Persoanlly, I'd avoid that thermaltake power supply...it should work, but its a bit low on 12v IMO. 

RAM is similar, its neither friendly or unfriendly. Some motherboards like some types/brands RAM, and dislike others, thats the main issue with RAM.  

Now for the annoying bit, sorry. 

That motherboard should work fine with linux, and the CPU should work fine with any distro that is fairly new. But, the motherboard and CPU are not comptible (CPU is socket 1156, motherboard is socket 775). 

The WD 'EARS' series drives do work, but they use 4k sectors, not the standard 512b sectors. They can be a real pain to setup, as you need to get any partitions 'alinged'. There is no warning if the partitions are not aligned, and there can be issues (the best of which is slower than standard perfromance, and it could affect the long term lifespan of the drive). 

BTW, I'd go for an AMD setup, you get more 'bang for your buck'. You can get a quadcore athlon II for less than a i5 dualcore.

---

### Post by coffeecat on 2010-10-06
> **cascade9 said:**
> The WD 'EARS' series drives do work, but they use 4k sectors, not the standard 512b sectors. They can be a real pain to setup, as you need to get any partitions 'alinged'. There is no warning if the partitions are not aligned, and there can be issues (the best of which is slower than standard perfromance, and it could affect the long term lifespan of the drive). 

@Sam3280, here's some more information on 4k sectors which might be helpful.

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

> **cascade9 said:**
> BTW, I'd go for an AMD setup, you get more 'bang for your buck'. You can get a quadcore athlon II for less than a i5 dualcore.

+1

There's another reason I went for an AMD system the last time I built one. I don't know about the socket 1156, but the socket 775 has a ridiculous (last time I looked) design of push pins for fitting the CPU cooler. Perhaps some coolers are better than others, but I know some  could be difficult to fit with very tight-fitting push pins. There's a much more intelligent design for the cooler bracket with AMD sockets.

---

### Post by Sam3280 on 2010-10-06
Ive always tended towards intel for no real reason but amd are better value, Here are some modifications, i will add a graphics card as well

quad core for around the same price as i3
AMD Athlon II X4 Quad Core 640 3.0GHz Processor - Propus Core - 45nm Manufacturing Technology - 4x 512KB L2 Cache - 95W Power - Socket AM3 (ADX640WFGMBOX)

[http://www.mwave.com.au/sku-19040185-AMD_Athlon_II_X4_Quad_Core_640_3_0GHz_Processor_-_Propus_Core_-_45nm_Manufacturi](http://www.mwave.com.au/sku-19040185-AMD_Athlon_II_X4_Quad_Core_640_3_0GHz_Processor_-_Propus_Core_-_45nm_Manufacturi)

ASUS M4N68T-M V2, Socket AM3, DDR3-1800, nForce 630a, HT 3.0, Onboard GeForce 7050PV, VGA, 4x SATA, 1x IDE, 1x PCIe x16, 1x PCIe x1, 2x PCI, 10x USB, Gigabit LAN, 8ch VT1708S, Micro ATX

[http://www.mwave.com.au/sku-28010686-ASUS_M4N68T-M_V2_Socket_AM3_DDR3-1800_nForce_630a_HT_3_0_Onboard_GeForce_7050PV_](http://www.mwave.com.au/sku-28010686-ASUS_M4N68T-M_V2_Socket_AM3_DDR3-1800_nForce_630a_HT_3_0_Onboard_GeForce_7050PV_)

Should I avoid Western Digital or go with a smaller HDD with 16MB cache:

Western Digital AV-GP 500GB Green Power AV Hard Drive, 32MB Cache, SATA 3Gb/s, IntelliPower (WD20EVDS)
[http://www.mwave.com.au/sku-22040382-Western_Digital_AV-GP_500GB_Green_Power_AV_Hard_Drive_32MB_Cache_SATA_3Gb_s_Inte](http://www.mwave.com.au/sku-22040382-Western_Digital_AV-GP_500GB_Green_Power_AV_Hard_Drive_32MB_Cache_SATA_3Gb_s_Inte)

---

### Post by Sam3280 on 2010-10-06
Thanks i kind of understand the 4k thing, is it better to avoid western digital

---

### Post by Sam3280 on 2010-10-06
Seagate Barracuda 7200.12 - 3.5" - 1TB HDD, SATAII, 7200rpm, 32MB Cache (ST31000528AS)
[http://www.mwave.com.au/sku-22040334-Seagate_Barracuda_7200_12_-_3_5_quot_-_1TB_HDD_SATAII_7200rpm_32MB_Cache_%28ST3100](http://www.mwave.com.au/sku-22040334-Seagate_Barracuda_7200_12_-_3_5_quot_-_1TB_HDD_SATAII_7200rpm_32MB_Cache_%28ST3100)

This HDD has really good reviews I think i will go with this

---

### Post by Sam3280 on 2010-10-06
Thank you for everyones help i think ive fixed everything up heres the graphics card ive chosen
Gigabyte Radeon HD 4550 Video Card - 512MB 64-bit GDDR3 RAM - 600 / 1600Mhz Clocks - PCIe 2.0 - HDMI, D-Sub, DVI - Low Profile Ready (GV-R455HM-512I)
[http://www.mwave.com.au/sku-42060479-Gigabyte_Radeon_HD_4550_Video_Card_-_512MB_64-bit_GDDR3_RAM_-_600__1600Mhz_Clock](http://www.mwave.com.au/sku-42060479-Gigabyte_Radeon_HD_4550_Video_Card_-_512MB_64-bit_GDDR3_RAM_-_600__1600Mhz_Clock)

---

### Post by mastablasta on 2010-10-06
> **cascade9 said:**
>  
The WD 'EARS' series drives do work, but they use 4k sectors, not the standard 512b sectors. They can be a real pain to setup, as you need to get any partitions 'alinged'. There is no warning if the partitions are not aligned, and there can be issues (the best of which is slower than standard perfromance, and it could affect the long term lifespan of the drive). 

 
WD uses a 3rd party software to get alignment in winxp. Is there no such really easy to use with nice GUI utility for Linux?
 
I second the AMD.
 
AMD cards (ex. ATI) will work with linux, however some reported issues due to their graphic card drivers being out of touch with linux reality :-)
seriosuly... i saw some issues reported and i've seen one manifest itself live... but i also have 2 computers at home with ATI where linux works flawlesly. 
 
ATI doesn't support it's cards with official drivers for long and they tend to be a bit more closed. others will advise better here but maybe Nvidia seems the way to go for better out of box experience. 
although i am staying with my ATI for now...
 
i would suggest you search if anyoen had any issues with this card and if they managed to solve them in simple way (if they had any).

---

### Post by coffeecat on 2010-10-06
> **Sam3280 said:**
> Gigabyte Radeon HD 4550 Video Card - 512MB 64-bit GDDR3 RAM - 600 / 1600Mhz Clocks - PCIe 2.0 - HDMI, D-Sub, DVI - Low Profile Ready (GV-R455HM-512I)
[http://www.mwave.com.au/sku-42060479-Gigabyte_Radeon_HD_4550_Video_Card_-_512MB_64-bit_GDDR3_RAM_-_600__1600Mhz_Clock](http://www.mwave.com.au/sku-42060479-Gigabyte_Radeon_HD_4550_Video_Card_-_512MB_64-bit_GDDR3_RAM_-_600__1600Mhz_Clock)

Before anyone chips in with "no, go for nvidia" I can tell you that my ATI Radeon HD 4350 gives me more than adequate 3d acceleration for compiz with the open source driver in both Lucid and Maverick. I tried the proprietary fglrx driver from the repository in Maverick and it worked just as well, except that it mucked up the Plymouth boot screen. :rolleyes:

I would hope your HD4550 would be just as compatible as my HD4350.

---

### Post by Sam3280 on 2010-10-06
I avoided nvidia but i dont really mind if there is I couldnt find any mention of it on the page about the graphics card

---

### Post by cascade9 on 2010-10-06
> **Sam3280 said:**
> Thanks i kind of understand the 4k thing, is it better to avoid western digital
 
 The 4k issue only happens with some of the 'Green Power' drives. They are good drives (I've got 1, but its a EADS 512b sector model, and my housemate has a EARS 4k sector model), but they just arent as quick as the caviar blue/black drives, which dont have the 4k problem. Well, not yet anyway, but the HDD industry is going to move to 4k sectors over time. Hopefully they fix the firmware on the drive so that they actually report the 4k sectors, that should fix the issue. 

> **mastablasta said:**
> WD uses a 3rd party software to get alignment in winxp. Is there no such really easy to use with nice GUI utility for Linux?

Not as far as I found. Maybe things have changed in a few months, but I doubt it.  

> **Sam3280 said:**
> Ive always tended towards intel for no real reason but amd are better value, Here are some modifications, i will add a graphics card as well

ASUS M4N68T-M V2, Socket AM3, DDR3-1800, nForce 630a, HT 3.0, Onboard GeForce 7050PV, VGA, 4x SATA, 1x IDE, 1x PCIe x16, 1x PCIe x1, 2x PCI, 10x USB, Gigabit LAN, 8ch VT1708S, Micro ATX

[http://www.mwave.com.au/sku-28010686-ASUS_M4N68T-M_V2_Socket_AM3_DDR3-1800_nForce_630a_HT_3_0_Onboard_GeForce_7050PV_](http://www.mwave.com.au/sku-28010686-ASUS_M4N68T-M_V2_Socket_AM3_DDR3-1800_nForce_630a_HT_3_0_Onboard_GeForce_7050PV_)


With that motherboard, you dont actually need a video card (its got one intergrated into the motherboard). 

If you do want a video card, then.....err......I'd consider changing the motherboard. The old nforce 630a chipset works fine, but its getting pretty long in the tooth now (its almost 4, which in chipset terms is like 120 years old). Also, the VIA 1708S sound chip is IMO horrible sounding. 

BTW, what is your intended use for your computer? That could change what parts you get. Eg- if you are intending to use your computer for much in the way of video watch, nVidia is the way to go (VDAPU, nvidia hardware video decoding, is a wonderful thing). I'm not doing the 'avoid ATI' thing, I quite like ATI, more than nVidia in some ways, just VDPAU is mature, stable, and works. As yet the ATI version is buggy and immature.

BTW- unless you actually have some reason to go to mwave, try this site- 

[http://www.staticice.com.au/](http://www.staticice.com.au/)

I'd be suprised if you cant find better prices there ;)

---

### Post by mastablasta on 2010-10-06
According to this article "parted" (gparted?!) could do the alingment as well as fdisk. still it's really a bit silly that linux is not prepared for this new tech.:
[http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives](http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives)

---

### Post by cascade9 on 2010-10-07
> **mastablasta said:**
> According to this article "parted" (gparted?!) could do the alingment as well as fdisk. still it's really a bit silly that linux is not prepared for this new tech.:
[http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives](http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives)

I'm 97% sure I tried that, and it didnt work. That might have been the version I was uisng though. 

If the drives actualy reported as 4k, not 'faking' 512b sectors the problem would be fixed from what I've seen.

---

### Post by Sam3280 on 2010-10-07
I wont get the graphics card, i didnt think the motherboard had GPU included

---

### Post by Sam3280 on 2010-10-07
Ok heres the final lineup going to check a few reviews before i buy


1 x 16011040 - Thermaltake V3 Black Edition Mid Tower Case With 450W PSU, SECC, 4x 5.25" Drive Bay, 1x Ext. 3.5" Drive Bay, 4x Int. 3.5" Drive Bay, USB x 2, HD Audio Ports (VL84521W2U) 

1 x 19040185 - AMD Athlon II X4 Quad Core 640 3.0GHz Processor - Propus Core - 45nm Manufacturing Technology - 4x 512KB L2 Cache - 95W Power - Socket AM3 (ADX640WFGMBOX) 

1 x 28010589 - Gigabyte GA-MA74GMT-S2, Socket AM3, Dual DDR3-1333, AMD 740G+SB710, HT 2.0, Onboard Radeon HD 2100, VGA, DVI, 4x SATA, 1x IDE, 1x FDD, 1x PCIe x16, 1x PCIe x1, 2x PCI, 10x USB, Gigabit LAN, 7.1ch ALC888B, Micro ATX (GA-MA74GMT-S2) 

1 x 37140119 - Kingston 2GB PC3-8500 (1066MHz) DDR3 ECC CL7 DIMM (KVR1066D3E7/2G) 

1 x 22040334 - Seagate Barracuda 7200.12 - 3.5" - 1TB HDD, SATAII, 7200rpm, 32MB Cache (ST31000528AS) 

1 x 17040338 - Samsung SH-S223C Internal 22x Speed SATA Dual Layer DVD-Rewritable, DVD±RW Drive 12x, DVD-RAM 16x, +R DL 12x-R DL, Black (SH-S223C/BEBF)

---

### Post by cascade9 on 2010-10-08
Much nicer motherboard IMO.

I'd really try to get at least DDR3 1333, thats pretty much the standard speed.

---

