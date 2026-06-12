---
title: "Replacing hardware"
date: 2008-10-26
forum: Hardware
---

### Post by mark0495 on 2008-10-26
Hello everybody! 

As we all know, there comes a time all your hardware is going to get old, and you have to replace your system with fresh (or at least, newer) hardware. That time is starting for me.... right now! I only would like to hear your advice. First I had my good ol' Kubuntu. In a few days the standard for Kubuntu is KDE 4.1, which is far too heavy for my poor system. That's why I decided to make the step to the regular, GNOME Ubuntu. What I found there is that even in this light distro, my computer is slower than it used to be. Shame! Xubuntu even works SLOWER than Ubuntu, which means there is one option left: hardware renewal! Below is a list of my hardware.

Computer: Compaq Presario 5686, 32 bits
Motherboard: Compaq 04E8h
CPU: Intel Pentium III Katmai 450 MHz
System memory: 320 MiB
Graphic card: NVidia Riva TNT
Sound card: Aureal Semiconductor Vortex 1
Ethernet card: 3COM Tornado 3c905C-TX/TX-M

I don't know if it's sufficient, but in an old broken computer I've got an NVidia GeForce 4 MX 4000. Please tell me what is too old, and suggestions what piece of hardware could replace it.

Thanks already,
Mark0495

---

### Post by nixscripter on 2008-10-26
First, I would simply say that it's probably the graphics card that needs to be upgraded. I've gotten older machines to run Linux quite well.

All I can suggest is my favorite cheap video card which can do anything with 2-D graphics I ask it: an ATI Radoen 9800 Pro. $40 to $60 bucks on the internet.

The other question is, how much memory does it have? The short way to find out is to run in a terminal: ```
cat /proc/meminfo | grep MemTotal
```

---

### Post by ardvark71 on 2008-10-26
Hi Mark...

I agree with Nixscripter. The other question is what you can upgrade *to.* I was able find your system's specs here...

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00013836&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00013836&dlc=en)

Unfortunately, you don't have a lot of room to work with. :( Your memory is upgradeable to 384 MB's of memory and you're restricted to a 2x AGP card, whatever you choose to get using this type of port. You mentioned you have a NVidia GeForce 4 MX 4000 card. If it's not a PCI card, you would have to make sure it's 2x backwards compatible.

EDIT: According to this page, it's 8x, which, if I remember correctly, the card would require a different type of AGP port, you would need to check the number of gaps on the section of the card that fits into the expansion port. :( 

[http://www.directron.com/mx400064agp.html](http://www.directron.com/mx400064agp.html)

I'm not sure what the specs of your Riva are but here are two cards that *might* work with your system. I think both are pretty much the same but one is cheaper and comes from another Compaq...

[http://www.alancomputech.com/190349-b21.html](http://www.alancomputech.com/190349-b21.html)

[http://www.ascendtech.us/itemdesc.asp?ic=VC32NVI6001743&eq=&Tp=](http://www.ascendtech.us/itemdesc.asp?ic=VC32NVI6001743&eq=&Tp=)

Any newer, more functional card is going to at least require 4x/8x compatability. You might be better off investing in a newer system. :(

Hope this helps...

---

### Post by starcannon on 2008-10-27
Heres the help docs on Ubuntu 8.04 system requirements; by looking at it, your right, your system is starting to show its age.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You have some options; I list in my opinion the order of best result

[LIST=1]
[*]. Build a new system from the ground up, yeah I know its a lot of money, but your due, and by the look of it, your equipment doesn't owe you any money; you definitely got your bang for dollar out of it, and you will again on a new system.
[LIST]
[*]Heres a barebones for $115.00 buy a cpu, some ram, a hard drive, and cannabalize a few parts off your old system and your in business
[/LIST]
 
[*]Go to an older version of Ubuntu, the latest know performer for your hardware, or go to a distro that specializes in Hardware of your computers era.
[*]Try Fluxbuntu, its VERY lite, I've run it on as little as a 366mhz celeron m with 256mb of ram and a 2 or 4 (i forget which) mb video card. It was super fast, and super stable.
[/LIST]
Good Luck and have fun.

---

### Post by mark0495 on 2008-10-27
Thank you all! I think it's time to save money for a new computer system. Fortunately, I saw a very nice webshop which delivers Ubuntu pre-installed computers for quite low prices. The lowest price is 198 euros (254 dollars if you covert it to U.S. Dollars) for a computer with AMD Sempron LE1200, or Intel computer with an Intel E2180 Dual Core for 228 euros (292 dollars converted). Does anyone know what's the best buy and what the (dis)advantages of an AMD system vs. an Intel system with Ubuntu are? 

EDIT: nixscripter, this is the output of your command:
```
MemTotal:       319476 kB
```

Thanks already and thanks for everyone who replied so quickly!
Mark

---

### Post by ardvark71 on 2008-10-27
> **mark0495 said:**
> Does anyone know what's the best buy and what the (dis)advantages of an AMD system vs. an Intel system with Ubuntu are? 


Hi Mark...

On the surface, I would be inclined towards the Core Duo, however, I would need a bit more information such as whether desktop or notebook, motheboard brand and model (and chipsets such as north and Southbridge,) memory, video, sound and network, including wireless. :)

Best Regards...

---

### Post by mark0495 on 2008-10-30
Okay, 


AMD LE1200 
Processor: AMD Sempron LE1200
Harddisk: 160 GB Sata II 
RAM Memory: 1GB DDR2 Kingston
Motherboard: ASUS
Video: onboard
Sound: onboard
Network card: onboard
USB 2.0: 4 x backside  / 2 x front
DVD/RW Combination

198 Euros


INTEL E2180 
Processor: INTEL E2180 dual core
Harddisk: 160 GB Sata II 
RAM Memory: 1GB DDR2 Kingston
Motherboard: ASUS
Video: onboard
Sound: onboard 
Network card: onboard
USB 2.0: 4 x backside  / 2 x front
DVD/RW Combination

228 euros

They are both desktop PCs. This is all the information I could find.

Mark

---

### Post by mark0495 on 2008-11-01
Hello again!

Thank you all for your fantastic replies! My problem is solved for now; I'm going to save money for a new system, and my computer is running Xubuntu 8.10 now, which seems to be much faster than 8.04 on my box. Still, I would like to know which of the computers I should buy, but that is a question for later on. Thank you all!

Mark0495

---

### Post by ardvark71 on 2008-11-01
> **mark0495 said:**
> Hello again!

Thank you all for your fantastic replies! My problem is solved for now; I'm going to save money for a new system, and my computer is running Xubuntu 8.10 now, which seems to be much faster than 8.04 on my box. Still, I would like to know which of the computers I should buy, but that is a question for later on. Thank you all!

Hi...

You're a funny guy! :p

The two systems you mentioned seem identical on the surface but again, I don't know the other chipsets. However, I'm a bit partial to Intel (for some reason,) so my opinion is going to be a bit biased. ;)

1. For the Intel Core Duo, The reviews here...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116052](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116052)

[http://www.pcworld.com/shopping/reviews/prtprdid,46646194-sortby,retailer/reviews.html](http://www.pcworld.com/shopping/reviews/prtprdid,46646194-sortby,retailer/reviews.html)

[http://compare.intel.com/pcc/showchart.aspx?mmID=890244&familyID=1&culture=en-US](http://compare.intel.com/pcc/showchart.aspx?mmID=890244&familyID=1&culture=en-US)

...rate this processor very well. However, I've already read on two of them that the stock fan is pretty noisy so you may want to invest in a new heatsink/fan assembly. Also according to these reviews, the processor overclocks nicely and has low power consumption. however, it is not a Core Duo 2.

For the AMD Sempron...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103195](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103195)

[http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_11599_11604,00.html](http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_11599_11604,00.html)

...not much that I found other than its low power consumption and its suitability for basic computing. :confused:

I'm not a processor "specialist" or do any overclocking so I can't comment on their capabilities apart from what is shown in the links.

Your main concern with Ubuntu, in part, is going to be what chipsets ASUS used in whatever devices it included on the board, namely graphics and sound. You might want to get the board model and number and research it here on the forums and on Google. Also, be sure there is some measure of expansion capabilities with these boards, i.e, PCI, PCIe, AGP) in case you want to upgrade or add new components. ;)

Hope this help. :)

Best Regards...

---

