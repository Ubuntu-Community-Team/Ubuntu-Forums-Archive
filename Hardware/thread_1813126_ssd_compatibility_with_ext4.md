---
title: "ssd compatibility with ext4"
date: 2011-07-27
forum: Hardware
---

### Post by coolgenes on 2011-07-27
Hi all,
I'm trying to assemble a computer that can be massively overclocked  as some of the software biologists have to use is not parallelized and so I really need to get either one really fast processor or in other cases they are very ram intensive.  the rest of my system specs will follow at the end, but right now I think my achilles heel may be the ssd used as a boot drive.  I would like to use the OCZ RevoDrive 3 series RVD3-FHPX4-240G for it's reported 1k Mb/s read/write speed.  it seems from some reviews that it does not support ext4 but I can't be sure b/c those post are pretty vague.  Does anyone have any experience with this?  another alternative, though half the speed is the Patriot Wildfire PW240GS25SSDR.  has TRIM been enabled on these yet?  Is this a problem for Linux?

other specs: ASUS P8Z68 Deluxe,Intel Core i7-2600 Sandy Bridge 3.4GHz, G.SKILL Ripjaws X Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 2300 (PC3 18400), IN WIN Dragon Rider case, using the video on the processor b/c not doing any intensive video editing (does this chew up processor time?), either Thermaltake CLP0575 or liquid cooling (comments?)

---

### Post by coolgenes on 2011-08-09
bump?

---

### Post by psusi on 2011-08-09
The filesystem has nothing to do with it; ext4 works just fine on an SSD, as does any other fs.

It sounds like that revodrive thing is not an SSD, but rather a pci express flash device.  Since it does not show up as a SATA hard disk, it requires proprietary drivers, which are windows only.

I may be wrong though, so if it does show up like a hard disk, then there's no reason ext4 won't work on it.

---

