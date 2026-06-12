---
title: "Ubuntu compatible SATA2 RAID card"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by Robvdl on 2007-10-29
I want to setup Ubuntu in RAID0 mode, but I would like to use hardware RAID, not software RAID.

The reason for this is, I dual boot Windows and Ubuntu. Ubuntu is my main day to day OS, Windows mainly for games. Now if I setup software LVM (which I have done so before), then only Ubuntu is running under LVM and not Windows, which is not what I want.

I have been in this situation a few times before with some of my friends PC's, and had once purchased a cheap RAID card which claimed to be "Red Hat Linux 8" compatible. I ended up buying a Lemon. At the time, Edgy was the latest version of Ubuntu, and it recognised the array as two SATA drives, instead of a single drive. I was very dissapointed.

Now my NForce board is the same, it has onboard RAID, yet Ubuntu recognises it as two drives last time I tried.

Now I see other people have asked this question in the forums before, yet never got an answer. I can get this Adaptec card, which is PCI Express 4 lane (that should go in my little PCI express slot, right?) and claims to be Red Hat Linux and Suse Linux compatible. Here is a link:

[http://www.myshopping.com.au/PR--199793_Adaptec_2241000_R_RAID_1430SA_ROHS_Single_Controller](http://www.myshopping.com.au/PR--199793_Adaptec_2241000_R_RAID_1430SA_ROHS_Single_Controller)

But will it work with Ubuntu??

Then another possibility, although a little more expensive is this one from Highpoint. It claims it supports Linux and BSD and supports INT13 BIOS booting.

[http://www.ascent.co.nz/productspecification.aspx?ItemID=349592](http://www.ascent.co.nz/productspecification.aspx?ItemID=349592)

Anyone know of a PCI SATA 2 RAID card that is known to work in Ubuntu, would be great. I don't really want to buy another $300 NZD lemon.

---

### Post by Robvdl on 2007-10-29
I read an interesting note on the HighPoint website:

The card I was looking at claims to have open source drivers (good on them!)

It also says under their FAQ:

Question: Which flavors of Linux are supported?

We provide pre-compiled driver packages for several popular Linux distributions such as Red Hat, RH Enterprise, Fedora, SuSE. We also provide driver source code that can be used to build the driver on other Linux distributions, and kernel versions where a pre-compiled binary is not provided.

These drivers are posted on our website, under the support-BIOS+Driver update section for each host adapter product.

...So even if this RAID card doesn't work "out of the box" with Gutsy, I should be able to compile a custom kernel, but then the question is, is it possible to compile a custom kernel before you have even installed Ubuntu?

---

