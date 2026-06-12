---
title: "wondering about adapter expresscard 34 to USB 3"
date: 2015-11-29
forum: Hardware
---

### Post by a-you on 2015-11-29
Dear forum moderators: if you decide to delete this then no hard feelings at all. I ask here because as one who adores using (in my case) ubuntu studio I've come to admire just how much people here know, and I haven't had any success getting the answer anywhere else.

I have a sony vaio VPCF116FX and it has an expresscard 34 slot. I'd like to get an adapter for that so I have a USB 3 port on this 2010 era laptop. But according to what I've read the speed of USB 3 requires an expresscard port that's 2.0. Info on this is vague but possibly that version was only in use by late 2010. I bought mine in spring of 2010. I wonder if my expresscard slot is going to be fast enough to support USB 3 or whether an adapter would be a waste of money/time.

I'm wondering whether anybody had any experience using such an adapter (specifically to USB 3) with gnu/linux on a laptop, especially if that's with a vaio like mine??

Thanks in advance!

---

### Post by kurt18947 on 2015-11-29
I bought a generic device off Ebay in June 2015. I plugged it into two machines, it worked in both so I put it back in the factory packaging. I bought a new USB 3 hard drive enclosure a few days ago so plugged this card in. Nothing. It shows up in lspci but no usb device recognizes it. I looked at alternatives and there aren't many. The one I have is from Renesas(spelling?) corp. though it is unbranded.  When I was shopping it appeared that a NEC chipset was key to getting a device to work with linux.

---

### Post by a-you on 2015-11-30
Thanks kurt. I guess I'll have to do some research then looking for an adapter that has an NEC chipset. Good to know. When I have any news I'll post it here.

---

### Post by kurt18947 on 2015-12-13
Update:  I had some spare time so messed with my Ebay generic expresscard-USB3 device. I had been using it in Ubuntu-Mate and had the card and a flash drive plugged in. I had to leave for a bit so put the system - with non-responsive adapter plugged in - in suspend. When I returned I pressed the power switch and the plugged in USB drive started flashing. Repeated suspend-resume cycles confirmed that if I plugged in a USB3 device and did a suspend-resume cycle or restart the card and its plugged in device was recognized. Just plugging in a USB device while running did not recognize the device.  I then booted a Mint Mate USB drive. Mint Mate recognized the expresscard USB adapter as expected including mount/dismount. There's something flaky with Ubuntu-Mate, not necessarily the card.

---

### Post by a-you on 2015-12-14
I haven't gotten an expresscard adapter yet. I'll post what happens when I do. Just didn't have time to yet. Thanks again for this info though because every bit of news helps.

---

### Post by furtom on 2015-12-14
> **kurt18947 said:**
> Update:  I had some spare time so messed with my Ebay generic expresscard-USB3 device. I had been using it in Ubuntu-Mate and had the card and a flash drive plugged in. I had to leave for a bit so put the system - with non-responsive adapter plugged in - in suspend. When I returned I pressed the power switch and the plugged in USB drive started flashing. Repeated suspend-resume cycles confirmed that if I plugged in a USB3 device and did a suspend-resume cycle or restart the card and its plugged in device was recognized. Just plugging in a USB device while running did not recognize the device.  I then booted a Mint Mate USB drive. Mint Mate recognized the expresscard USB adapter as expected including mount/dismount. There's something flaky with Ubuntu-Mate, not necessarily the card.

I have noticed that ubuntu mate is not great at reading USB devices in general. In my case, a wifi stick. Flaky is the perfect word.

I was all set to go into search mode and track the problem down, figuring an updated driver was to blame, when suddenly, it just started working. ifconfig, iwlist etc all look good... so i put it asside.

since then, i've noticed other usb devices will occasionally go in and out. sometimes they are recognized, sometimes not. I'd love to file a bug report, but I can't duplicate it!

I'll try suspend/resume next time!

---

### Post by kurt18947 on 2015-12-16
> I have noticed that ubuntu mate is not great at reading USB devices in general. In my case, a wifi stick.

Wifi adapters can come with their own set of issues. Adapters using RealTek RTL8188**/8192** are an example I'm familiar with. The native linux drivers work but are imperfect.

---

### Post by furtom on 2015-12-16
> **kurt18947 said:**
> Wifi adapters can come with their own set of issues. Adapters using RealTek RTL8188**/8192** are an example I'm familiar with. The native linux drivers work but are imperfect.

Perhaps. As I say, these problems are not easially duplicatable and therefore my observations are not scientific. 

However, for my money, there is more going on than that. All other flavors of ubuntu do not have any issue with my setup. It defies logic that a DE would affect a hardware driver, but then again that's why they call them bugs.

The fact remains, if I'm runing lubuntu, xubunte or ubuntu, I can go years without incedent. However, as soon as I install Mate (weather or not I'm actually running the DE) the weird problems begin. And I've noticed this since the very first time I installed Mate, several years ago.

If it was more than an occasional annoyance, I'd try harder to track it down. But it is really happening!

---

### Post by a-you on 2016-01-07
Just a quick note to say that I still haven't gotten that adapter, in case anybody was wondering. I'll post my results when I do but it may be a while. Just haven't needed it very urgently.

---

