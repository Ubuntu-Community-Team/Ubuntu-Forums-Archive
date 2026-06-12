---
title: "A doubt about drivers of some components in Ubuntu"
date: 2015-11-19
forum: Hardware
---

### Post by edu_3716 on 2015-11-19
Hi,

I'm new in this forum. The reason why I'm asking here is the next:

I work in a bioinformatics laboratory and I need to use a set of software to work on data analyses; and they are thought to work on Unix. So I'm interested to buy a moderately powerful computer and I'm worried if Ubuntu will have the drivers of the next components:

[B]InterCoreI7-5820K 3,3Ghz Hexa Core
ASUS X99-A
ASUS GeForce GTX750 Ti 2Gb GDDR5
[/B]DVD LG GH24NSC0
TP-LINK TL-WN881ND Wireless N 300


There is some place where I can check that? In the case that Ubuntu doesn't come with that drivers, there is usually easy to download and install drivers in Ubuntu? (I have a basic knowledge of Linux).

Thanks!!!

Edu

---

### Post by Mark Phelps on 2015-11-19
Looks like you need a specific set of applications to work -- so before worrying about hardware for Linux, you should first check the websites of the apps you want to run and find out WHICH specific Linux distros and versions the are compatible with.

Linux is just an OS kernel; what you install is a distribution (abbreviated distro) which is a set of system software, applications, and a default desktop UI.

There are two general packaging systems for Linux distros -- RPM and Debian -- and they are not compatible or interchangeable.  Some folks will tell you that running Alien will allow you to convert RPM packages to Debian packages, but that only works in an very limited fashion.

Not all distros are alike, in fact some are very different.  So, if the apps works in Open SUSE, it will likely NOT work in Ubuntu.   The Distro version is very important as is the Release.  For example, if something used to work in Ubuntu 12.04, it might not work in Ubuntu 15.10.

Once you find that out from the app websites, then let us know what distros will work and we can proceed further.

---

### Post by weatherman2 on 2015-11-19
You can always boot Ubuntu "live" from USB without installing it on any hardware, to see how it works.

Naturally, if you are about to order a computer (or components) via mail and not at a retail store, you can't very well boot an OS first to try it.  But, you could read the reviews of various components and look for mentions of Linux or Ubuntu.  I find the reviews on Newegg's website seem to have a lot of Linux users posting reviews so look for their reviews for various components.

You can dig deeper than just a product model name and find out the chipsets used in each.  Linux doesn't support a graphics card directly; it supports the chipsets on it.  Find out what chipset is used on the ASUS GeForce GTX750 and then see how well that chipset is supported.  Same with the motherboard chipset.

I suspect the wireless card is likely to be the biggest challenge, but FYI that's probably the easiest thing to work around with a desktop computer.  Unless the wireless card is built right into the motherboard, it may be easy to change it for a more compatible wireless card.  Some newer motherboards use the same mini-PCI slots used in laptops, so you can simply buy a more compatible wireless card on eBay if the one that comes with the motherboard does not work well in Linux.

I would try to stick to an LTS version of Ubuntu, by the way, for stability purposes.  Ubuntu 14.04 LTS will be supported until 2019, but Ubuntu 15.10 is only support for nine months - then you will have to upgrade.  The LTS versions get upgraded kernels every so often, so now you can use Ubuntu 14.04.3 which has a newer kernel than the original Ubuntu 14.04 release and that kernel is more likely to have better hardware support for newer hardware.

---

### Post by Yellow Pasque on 2015-11-19
I'd be most worried about the wireless card. The rest looks fine. The GTX750 may not fully function "out of the box" with the open source nouveau driver, but it is easy to install the nvidia driver with this PPA: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

> TP-LINK TL-WN881ND Wireless N 300
Do you know what chipset it uses?
EDIT: I see some reviews on newegg that claim it works fine with LInux.

---

### Post by edu_3716 on 2015-11-20
Thank you for the replies!

> Looks like you need a specific set of applications to work -- so before worrying about hardware for Linux, you should first check the websites of the apps you want to run and find out WHICH specific Linux distros and versions the are compatible with.
All the software that I'm interested to use works fine with the Ubuntu, and due that I'm a little bit familiarized with this Unix distribution, I will continue using this one.


> Ubuntu 14.04 LTS will be supported until 2019, but Ubuntu 15.10 is only support for nine months - then you will have to upgrade. The LTS versions get upgraded kernels every so often, so now you can use Ubuntu 14.04.3 which has a newer kernel than the original Ubuntu 14.04 release and that kernel is more likely to have better hardware support for newer hardware.
OK!


> I'd be most worried about the wireless card.

I read in different websites that it seems to work find in Linux (chipset: Atheros AR9287). 

> I suspect the wireless card is likely to be the biggest challenge
Why you expect that the wireless card could be more problematic than the rest of the components? Unix tends to support both motherboard and processors more than the wireless card? Regarding to motherboard and processors, where can I check the chipsets? In the developer's web page? And in the case I find the chipsets, where I can check if the distribution of Ubuntu that I want to use (e.g. Ubuntu 14.04 release) have the drivers for these chipsets?


> The GTX750 may not fully function "out of the box" with the open source nouveau driver, but it is easy to install the nvidia driver with this PPA: [https://launchpad.net/~graphics-driv...ive/ubuntu/ppa](https://launchpad.net/~graphics-driv...ive/ubuntu/ppa)
Ok!

-

Edu

---

### Post by coldraven on 2015-11-20
Get your 14.04.3 here (scroll down the page for download options and checksums)
[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

---

### Post by grahammechanical on 2015-11-20
> Why you expect that the wireless card could be more problematic than the rest of the components?

It is because the developers of the Linux kernel try to keep up to date with hardware developments and provide driver modules as part of the kernel. So, it is very rare for a user to need to install motherboard & chipset drivers after installation. 

It often is not necessary for a user to install a WiFi driver either. But with some WiFi adapters we do need to install a driver after installation. This is why there is a little concern about WiFI adapters. Ubuntu has a utility called Additional Drivers that may offer a WiFi driver after installation.

Another area of concern is the video adapter. Again Additional Drivers can help out with installing a proprietary video driver. But if the video adapter is very new and Ubuntu has not caught up we may need to install a proprietary video driver from a Personal Package Archive (PPA) or from the manufacturer's web site. That is if, the manufacturer has seen fit to provide a Linux driver to support that very new video card. Sometimes we have to wait a bit.

Oh, by the way. we can install drivers onto a live session. For WiFi drivers we would need to be connected by ethernet cable.

Regards.

---

### Post by edu_3716 on 2015-11-20
Very clear and useful info. Thanks!

---

### Post by Yellow Pasque on 2015-11-20
Wifi drivers tend to be a bit problematic depending on the chipset manufacturer. Sometimes, they need proprietary drivers. Sometimes, they require the user to build and install a newer kernel module. Atheros is one on the more Linux-friendly vendors though.
Also, as graham pointed out, if you can't connect the system (at least temporarily) via ethernet, troubleshooting is a pain.

---

