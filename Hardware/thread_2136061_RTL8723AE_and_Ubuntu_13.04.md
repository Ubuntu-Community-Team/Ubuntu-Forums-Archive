---
title: "RTL8723AE and Ubuntu 13.04"
date: 2013-04-16
forum: Hardware
---

### Post by NuttyPro67 on 2013-04-16
I have an IdeaPad Yoga 13 with a realtek RTL8723AE wireless adapater.

I have been unable to get the wireless to work at all.

I installed Ubuntu 12.10 64-bit edition and attempted to compile and use the drivers listed everywhere for the RTL8723AE but none of that worked.

Next, I installed Ubuntu 13.04 Beta since I read in several places that the RTL8723AE drivers were supported with the new kernel.

But even with 13.04 Beta (32 bit) installed, I've got nothing.  

Running lsusb shows the wireless adapter is detected:
Bus 001 Device 004: ID 0bda:1724 Realtek Semiconductor Corp.

But it's not working at all.  As far as Ubuntu is concerned, there are no wireless adapters on my laptop.

Kinda ran out of ideas here.  Maybe I need to install Ubuntu 13.04 64-bit instead of the 32-bit version?

---

### Post by kurt18947 on 2013-04-16
Here is a site I use for info about wireless devices:  [http://wikidevi.com/wiki/Realtek_RTL8723AE_Reference_Design](http://wikidevi.com/wiki/Realtek_RTL8723AE_Reference_Design).  It looks like native linux support is in the future for that device.  I have no idea about NDISwrapper.  You could get a 'known-to-work-out-of-the-box' USB adapter in the meantime if you're so inclined.  It's kinda handy to have one of those anyway.  There is a patch which is supposed to enable that chipset [http://www.spinics.net/lists/linux-wireless/msg96861.html](http://www.spinics.net/lists/linux-wireless/msg96861.html) but knowing how to incorporate such an animal is well beyond my abilities.  Chili 555 or Wild Man might be able to make sense of it, I might as well be looking at ancient Aramaic.

---

### Post by NuttyPro67 on 2013-04-16
Thanks for the reply, Kurt.  I'll look into those links you provided.

Hopefully support for this wireless card will find it's way into 13.04 before release.

---

