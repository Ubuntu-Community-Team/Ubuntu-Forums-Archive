---
title: "Error installing Ubuntu"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by yngndrw on 2009-10-31
Hi,

I'm trying to install Ubuntu to a new system, I'm unsure if this is a hardware, BIOS or general software error. I do have lots of images of settings and one of the error messages that Ubuntu has given me so I'm hoping that somebody would be able to help me out with this one.

First of all, the system:
* [Asrock A330GC](http://www.asrock.com/mb/overview.asp?Model=A330GC) (Intel Atom + Intel 945GC / ICH7)
* 512GB of PC-4200 DDR2 RAM, unbranded (I did have two of these, but one was DOA)
* [Super Talent 4GB Flash Disk Module](http://www.supertalent.com/products/ssd_category_detail.php?type=FDM) (The 40pin vertical version - SF4GB5Y40)

[Here is a picture of the system.](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009131.jpg) (Sorry about the bad focus.)

I've been installing:
* Ubuntu 9.10 Desktop (I386)
* Ubuntu 9.10 Netbook Remix (I386)

I first tried installing from a USB DVD drive. The drive isn't too reliable but it seemed to get just as far as installing from a pen drive. Since then I've been installing from a (Slow) 1GB pen drive. I used UNetbootin and [this guide](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/) to do the pen drive installations.

I have checked both downloads against the MD5 hashes so they are fine. I also tried installing Desktop straight from the .iso on to a Virtual Machine and it worked.

[Here is a picture of the error I've been getting.](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009130.jpg) I'm getting this after I've selected "Install" from the initial menu. It loads two files then throws that up on the screen.

Here are the BIOS settings: (Using the only BIOS version available.)
* [Main](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009132.jpg)
* [Advanced > CPU Configuration](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009133.jpg)
* [Advanced > Chipset Settings 1](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009134.jpg)
* [Advanced > Chipset Settings 2](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009135.jpg)
* [Advanced > ACPI Settings](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009136.jpg)
* [Advanced > IDE Configuration](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009137.jpg)
* [Advanced > IDE Configuration > IDE1 Master](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009138.jpg)
* [Advanced > Advanced PCI/PnP Settings](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009139.jpg)
* [Advanced > Configure Super IO Chipset](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009140.jpg)
* [Advanced > USB Configuration](http://yngndrw.hostilezone.net/uploads/ubuntuerror/31102009141.jpg)

I've tried changing:
* Hyper Threading
* DVMT Mode / Memory
* Memory Bandwidth Boost
* ACPI HPET Table
* ATA/IDE Configuration
* 32Bit Data Transfer

Any ideas ? I will try a different hard drive if I can find one spare.

Thanks,
-Andrew.

**Edit:**
It seems that both RAM sticks were broken. I'm very happy that Memtest was included on the Install CD as that is how I found the problem. I also like the fact that it now installs from within a "Live" version, but I suspect that I'm late in seeing this new feature.

---

