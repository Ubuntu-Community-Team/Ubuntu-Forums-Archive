---
title: "Install ubuntu on an old computer."
date: 2009-05-09
forum: Hardware
---

### Post by atliia on 2009-05-09
I have an old IBM I am not sure of the details but the sticker says 
```
Machine Type 6280 Serial No. 114XXXX
Model 15 U Config ID CF27398
```
This is a really old system that was originally running on Win ME. It was upgraded to XP however, I have not used it in about 5 years. I believe that the computer boots only from floppies. The hardest part of the install process is I can not get the monitor too work. I have, what I believe is the original disk to install the monitor, however I have not been able to get any thing to function. If anyone would be able to walk me through the set up and install of ubuntu on this computer I would be grateful.

---

### Post by whistlingtony on 2009-05-09
Boots only from floppies?

Installing on that machine will be a giant pain in your ***.

I'd recommend taking the hard drive out, getting an adaptor so you can connect the hard drive to a real computer, :D, and do your install there. When you're done, plop your hard drive back into the Elder Laptop and say a prayer to Cthulhu. It should work fine.

You can get the adaptors for pretty cheap. [http://www.google.com/products?q=laptop+to+IDE+adaptor&hl=en](http://www.google.com/products?q=laptop+to+IDE+adaptor&hl=en)

Good Luck!

-Tony

---

### Post by roger_1960 on 2009-05-09
Hi

See this page for specs:

[http://www.shopping.com/xPF-IBM-NetVista-A20-6280-628015U](http://www.shopping.com/xPF-IBM-NetVista-A20-6280-628015U)

Does it have a CD drive?

Video driver (for windows) is here:

[http://www.drivershq.com/Drivers/IBM/NetVista/6280/21347/23182/23222/99190/ModelDrivers.aspx](http://www.drivershq.com/Drivers/IBM/NetVista/6280/21347/23182/23222/99190/ModelDrivers.aspx)

If it does have just 64Mb of Ram it wont run Ubuntu of any sort.   You could try puppylinux via the floppy booting route.

---

### Post by atliia on 2009-05-09
It has a CD drive yes. I opened it up and it has 64MB of Infineon SDRAM. I am thinking about putting some mew ram in it inorder to support ubuntu then. Any suggestions on what else I should add while I am at it.

---

### Post by roger_1960 on 2009-05-09
Hi

Add at least 128Mb of Ram

Then you could install Xubuntu (I suggest 8.04 LTS) using the "alternative" CD (which is not a "live" CD and is a text based install) and it should run fine.

If you wish to run linux ( but not ubuntu based) try puppylinux from CD which should run fine without extra ram.

---

### Post by kerry_s on 2009-05-09
> **atliia said:**
> I have an old IBM I am not sure of the details but the sticker says 
```
Machine Type 6280 Serial No. 114XXXX
Model 15 U Config ID CF27398
```
This is a really old system that was originally running on Win ME. It was upgraded to XP however, I have not used it in about 5 years. I believe that the computer boots only from floppies. The hardest part of the install process is I can not get the monitor too work. I have, what I believe is the original disk to install the monitor, however I have not been able to get any thing to function. If anyone would be able to walk me through the set up and install of ubuntu on this computer I would be grateful.

with my ibm i have to add to xorg.conf driver section:
Option "BusType" "PCI"

or it will boot up blank. so you have to select the recovery mode, nano /etc/X11/xorg.conf and add that option.

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"BusType" "PCI"
EndSection

```

---

### Post by snowpine on 2009-05-10
Hi Atliia, that computer is not a good candidate for Ubuntu, unfortunately. I recommend upgrading to a computer with the following minimum specs, then you can enjoy Ubuntu as it was meant to be enjoyed:

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

---

