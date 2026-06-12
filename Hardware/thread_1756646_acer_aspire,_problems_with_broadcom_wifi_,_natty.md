---
title: "acer aspire, problems with broadcom wifi , natty"
date: 2011-05-12
forum: Hardware
---

### Post by clstal on 2011-05-12
Just got a acer aspire 1430z ([http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=2781](http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=2781)), installed natty, and am having a hell of a time getting the wifi to work.  It's a broadcom 943225 and as far as I can tell the STA broadcom driver is working for other people (can't find this netbook listed, but for the same broadcom card in another acer netbook, in karmic). ([https://help.ubuntu.com/community/Aspire1810TZ/Karmic](https://help.ubuntu.com/community/Aspire1810TZ/Karmic))  

I've uninstalled and reactivated the sta driver in "Additional Drivers" to no effect.  I've toggled the wireless off and on via Fn-F3 (the key combo that should turn the wireless on and off) with no change in lights (it should turn orange if wireless is on) or detection by ubuntu network manager.  

Help!

---

### Post by coffeecat on 2011-05-13
> **clstal said:**
>   It's a broadcom 943225 and as far as I can tell the STA broadcom driver is working for other people 

Do you mean the BCM43225? If so, that *should* be supported by the default new open source brcm80211 driver that comes with Natty. The brcm80211 works just fine for me with one of the other few Broadcom chipsets that it supports, but that's with a 32-bit install. I was involved in another thread where it was suggested that the brcm80211 driver might not be working properly in 64-bit, but unfortunately this question was never resolved. Which are you using 32 or 64-bit?

A suggestion. Boot up the live Natty CD, go to the live desktop and see if the wireless card works out-of-the-box with the brcm80211 driver. If yours is a 64-bit CD and it doesn't work, you could try downloading the 32-bit ISO and see if that works. Believe me, the brcm80211 driver "just works" without any fuss or bother for me. At first the system pestered me to install the STA driver, but I ignored it.

@theonlynameleft, yours is a different problem - you have a different make of wireless chipset, hence a different driver. I suggest you start your own support thread. Trying to deal with two different issues will only confuse this thread.

---

### Post by clstal on 2011-05-13
Coffeecat,

Yep, that's the one I got.  I tried both ways, STA and included driver and couldn't get it to work.  

I'm not sure WHY this worked but for whatever reason it did (same question posted to a different location, w/ more info): 

[https://answers.launchpad.net/ubuntu/+source/b43-fwcutter/+question/157259](https://answers.launchpad.net/ubuntu/+source/b43-fwcutter/+question/157259)

Blacklisting the acer-wifi manager didn't make the slightest bit of sense to me but I was desperate and trying random stuff and it worked. 

My thanks!
Crystal

---

