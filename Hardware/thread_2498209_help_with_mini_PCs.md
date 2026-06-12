---
title: "help with mini PCs"
date: 2024-06-04
forum: Hardware
---

### Post by recycleyourself on 2024-06-04
Hello,

I've been a Linux user in the past (Ubuntu, Mint) but had to switch back to Windows the past several years because I was doing a lot of collaboration at work using MS office products and the formatting just never seemed to translate over correctly from Word, and PowerPoint.  But now I have Office365 which makes that point moot.  I've recently used 365 on my main home pc with Ubuntu Live boot.  It was great.  Thought I'd enjoy getting back into the Linux world and maybe trying some other distros, finding something I liked and installing it on a separate PC from my home pc.  My wife and kids are not very positive about change and don't want anything but windows.

A number of years ago I remember seeing a fanless MintBox but it was too $$$ for me.  I thought now I'd find a new mini PC, maybe fanless, and use a KVM switch at our desk to make it easy to change between Windows for my family and Linux for me.

I bought a Minix Z83-4 Plus V2 (pro) at a good price.  It booted up with preinstalled Win10 no problem.  I then proceeded to try Ubuntu, Mint, Manjaro, and Peppermint....each promising at first then leading to a black screen during install for Liveboot.

Did a bit of digging and it seems it's related to GRUB efi being 32 bit vs 64bit?  I honestly don't understand it all.  There is someone named Linuxium that looks like they've made Ubuntu 22 install with their custom build, but again I'm just not understanding the process.

#1  Do you think this is even worth the effort
#2  Should I try and find different hardware in place of the MINIX.  If so, then what hardware?  I really like the idea of a mini PC.  I already have a tower for my main PC in our desk.  BUT....I don't want to buy another miniPC that isn't capable of installing Linux due to the 32 vs 64bit thing

---

### Post by oldfred on 2024-06-04
Is this an older system?
Linux years ago did not have a 32 bit UEFI boot loader. So some vendors (per Microsoft?) created lightweight systems that used a 32 bit bootloader on a 64 bit system to make it Windows only or lock out Linux.
But then Linux developed a 32 bit UEFI boot loader. But I have not seen much if any of these systems for years.

Older instructions have you compiling your own, but now you just need to download the 32 bit UEFI boot file.
Linux 3.15 Kernel Gains EFI Mixed Mode Support from 2014
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)

Ubuntu now is really for newer systems, you may find a lighter weight flavor works better.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
While Kubuntu is more full featured it also is not as heavy as Ubuntu. I have used it both on desktop, new laptop & very old 2006 laptop. Laptops used an external SSD with Kubuntu with essentially a copy of desktop install.

Some users have posted suggestions on lower end hardware, often then just for a server for backup. Even as low end as a Raspberry Pi.
Or purchase a 2 or 3 year old used system.
You can do like I do for my Windows laptop. I only have it for Taxes & travel. But have a $25 USB to NVMe adapter & NVMe drive (price varies by size) and have a full install of Kubuntu on it. When not plugged into laptop, it boots Windows, when plugged in, I can boot Kubuntu. And external SSD is almost as fast as internal SSD is.

---

### Post by him610 on 2024-06-04
> Key Features
1.44 GHz Intel Atom x5-Z8300 Quad-Core
4GB of DDR3L RAM
Integrated Intel HD Graphics
32GB of eMMC 5.0 Storage
> MiniX Z83-4 Specs
Operating System	Windows 10 Home (64-Bit)
Performance Graphics Type	Integrated 
Total Installed Memory	4 GB
Memory Slots	No
PCI Expansion	No
Optical Drive	No
Communications Wi-Fi	
Wi-Fi 5 (802.11ac); Dual-Band (2.4 & 5 GHz) 
This device has been on the market since 2017. There are better, more capable mini-pcs available now with more RAM; furthermore, some can be upgraded with added RAM and additional SSD.
With only 4GB, you might consider a lighter flavor like Lubuntu or Xubuntu.
With only 32GB of eMMC, Win10 probably takes up all of the space.

---

### Post by TenPlus1 on 2024-06-07
On such a low specced system you may want to try out Bodhi Linux 7.0 as it does run quite well on my Acer Cloudbook with 2GB memory.

---

### Post by egalvan on 2024-06-13
I am using Ubuntu 20.4 on the following USFF machines

Dell OptiPlex 3050 (i3, 16GB)
Dell OptiPlex 7050 (i5, 32GB
Dell OptiPlex 7060 (i7, 32GB)
Dell OptiPlex 7070 (i7, 32GB)
HP EliteDesk G3  (i5, 16GB)
HP EliteDesk G4  (i7, 32GB)
All have SSD and/or NVMe
These are all 1-liter sized Ultra Small Form Factor
Pricing ranged from $40 (lucky) to $160 (OptiPlex 7070)

some are mine, others belong to family members.
i&#8217;m upgrading two machines to 24.0 soonest.
the rest will be upgraded after verifying those upgrades&#8230; probably at the first dot upgrade.

---

