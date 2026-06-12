---
title: "*New* Dell Latitude 3450 &amp; Dell Wireless 1707"
date: 2015-04-23
forum: Hardware
---

### Post by chuck21 on 2015-04-23
I know that older versions of the Dell Latitude 3450 are supported by Ubuntu, according to the Ubuntu Desktop Certification page. However, it seems Dell has changed at least some components in their newer offerings.

In particular, the wireless card is now a Dell 1707 instead of an Intel 7265.

Does anybody know the level of support for that wireless card with Ubuntu? More generally, is there anything I need to know about these new 3450s (from early 2015)?

I'm thinking of buying one of these laptops, which are on sale at the moment, but the Dell service representative wasn't helpful with regard to Linux. I also haven't been able to find anything out on the internet.

---

### Post by weatherman2 on 2015-04-23
Do some sleuthing and figure out what the "Dell 1707" card really is.  Dell doesn't make wireless chipsets; it's probably an Atheros or Broadcom chipset.  And that's what really matters: is that chipset supported in the latest Linux?  If so, you should be OK - should be some way to make it work even if it doesn't work automatically at install.

It's also possible to buy an Intel card and replace the 1707 card at some point, if you want to.  Some laptops have easy-to-access internal wireless cards, and replacing them (at least in a Dell) may be easy.  Sometimes you get to the card by removing a panel on the bottom of the laptop with a few screws and there it is: pop off the antenna wires and swap the new card in and that's it.  Sometimes the wireless card is buried under the keyboard and difficult to get to.  Depends on the design of that particular model.

Of course, Dell will warn you that you void your warranty by doing this, but you don't have to tell them; you can keep the old card and put it back in (if it's easy) if you have to have the laptop fixed under warranty.

---

### Post by chuck21 on 2015-04-23
[COLOR=#333333][FONT=open-sans-1]Thanks Weatherman2,

I was able to find the following here: 
[http://dellwindowsreinstallationguide.com/driver-sets/dell-wireless-cards/](http://dellwindowsreinstallationguide.com/driver-sets/dell-wireless-cards/)

But I have no idea how to find out if this card is supported by Linux. If I understand you correctly, you're saying that even if I don't establish with certainty that it's supported, the risk is small enough that it's reasonable to go ahead and purchase the computer. Is that right?

Dell Wireless 1707 – 802.11bgn[/FONT][/COLOR]
[COLOR=#333333][FONT=open-sans-1]Hardware IDs:
PCI\VEN_168C&DEV_0036
PCI\VEN_168C&DEV_0036&SUBSYS_020E1028
Vendor: Atheros[/FONT][/COLOR]

---

### Post by salih-emin on 2015-05-23
> **chuck21 said:**
> [COLOR=#333333][FONT=open-sans-1]Thanks Weatherman2,

I was able to find the following here: 
[http://dellwindowsreinstallationguide.com/driver-sets/dell-wireless-cards/](http://dellwindowsreinstallationguide.com/driver-sets/dell-wireless-cards/)

But I have no idea how to find out if this card is supported by Linux. If I understand you correctly, you're saying that even if I don't establish with certainty that it's supported, the risk is small enough that it's reasonable to go ahead and purchase the computer. Is that right?

Dell Wireless 1707 – 802.11bgn[/FONT][/COLOR]
[COLOR=#333333][FONT=open-sans-1]Hardware IDs:
PCI\VEN_168C&DEV_0036
PCI\VEN_168C&DEV_0036&SUBSYS_020E1028
Vendor: Atheros[/FONT][/COLOR]

I can confirm that Ubuntu 14.04 runs out-of-the box with this card. I own a Dell Inspiron with [COLOR=#333333][FONT=open-sans-1]Dell Wireless 1707[/FONT][/COLOR]

---

### Post by Rob Sayer on 2015-05-23
It likely will work out of the box, though it may need some config, esp. some broadcom wireless adapters.

Even if it doesn't work you can get a cheap USB wireless dongle that *will* work in linux.  This is a much better solution for some wireless cards than trying to use the windows drivers with ndiswrapper.  So while wireless adapters are a relatively common hardware support issue, it's actually a pretty easy fix.

---

