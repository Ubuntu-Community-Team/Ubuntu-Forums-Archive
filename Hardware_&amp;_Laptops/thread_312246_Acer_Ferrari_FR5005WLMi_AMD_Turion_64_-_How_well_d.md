---
title: "Acer Ferrari FR5005WLMi AMD Turion 64 - How well does this work with ubuntu?"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by Josh1 on 2006-12-04
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2371648&CatId=1902](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2371648&CatId=1902)

Going to be getting this by xmas, how well does this work with ubuntu? Going to have a 120 gig partition for ubuntu, 40 gigs for windows (Windows = Photoshop CS2, Dreamweaver, Ubuntu = Everything else ;)).

Anyone used this for ubuntu?

---

### Post by mbobak on 2006-12-05
I have an Acer Ferrari 1000 (the one w/ the 12.1" screen), and I *love* it.

Here's what I've got working:
 - ATI binary drivers for accelerated 3D
 - wired ethernet (worked out of the box)
 - wireless 802.11n (worked with latest ndiswrapper (from svn) and drivers from ACER site
 - Sound (use ALC883 drivers from RealTek site)
 - Bluetooth Mouse (worked w/ install of bluez-* from Synaptic)
 - Synaptics TouchPad (worked out of box, works better if you track down and install specific Synaptics driver)
 - Full audio and video codecs, complete with DVD playback (thanks Automatix!)

I have read that the 5-in-1 card reader works out of the box, but I don't have any of the cards it supports, so I can't confirm that.

Also, the Bluetooth VOIP phone has not been tested.

Overall, I love Ubuntu on this laptop!

-Mark

---

### Post by mbobak on 2006-12-05
Oh, I should add, I'm doing it all w/ i386, not x86-64.  

I started w/ x86-64, but had difficulties, mainly, couldn't get wireless working.

Things are pretty slick w/ i386 though, and I have no real, compelling reason to move to 64-bit.

-Mark

---

### Post by Josh1 on 2006-12-07
Thanks for reply, going to be ordering it within the next couple of days :).

---

