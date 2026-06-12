---
title: "Recommendation for a cheap graphics card?"
date: 2012-04-18
forum: Hardware
---

### Post by OliverHaslam on 2012-04-18
I'm after a graphics card to replace the very old Geforce 6600 that is in my server.

I've just installed Windows 7 into a VM and I cannot give the thing enough RAM to run Aero, so I think it's time to upgrade.

It would be nice if I could run some games on it, but nothing exciting. I'd rather it be cheap than awesome.

Any recommendations for something we know works well with Ubuntu?

---

### Post by SeijiSensei on 2012-04-18
Almost any NVIDIA card with an 8xxx chip or better is a pretty good bet. I have an XFX card with a 9500GT processor that has worked continously for a couple of years now.  [Here](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100006519%2050001669%2040000048%20600030348&IsNodeId=1&name=NVIDIA) are the current XFX offerings from Newegg; three of them are around $40 with shipping.

The only problem may be finding a card that fits the slot on your machine.  If you only have PCI slots you may need to dig deeper to find a compatible device. The cheapest ones on that page require a PCI Express slot.

---

### Post by Andrew_P on 2012-04-18
> **OliverHaslam said:**
> I've just installed Windows 7 into a VM and I cannot give the thing enough RAM to run Aero ...

If you've run Vista or Windows 7 on a laptop computer with the Aero interface before, you'll know that it takes a tremendous amount of processing power, making both the CPU and the GPU run *hot*.:(  A few years ago I downgraded a Compaq laptop from the factory-installed Vista to Windows XP for this very reason.  With the Aero interface active, the computer's fan ran continuously and usually at maximum speed.  Battery life was ridiculously short.  The translucent look of Aero is a gimmick that isn't worth it, in my opinion.  Nonetheless, good luck in you search for a better video card.

---

### Post by MonkeyPaw on 2012-04-18
> **Andrew_P said:**
> If you've run Vista or Windows 7 on a laptop computer with the Aero interface before, you'll know that it takes a tremendous amount of processing power, making both the CPU and the GPU run *hot*.:(  A few years ago I downgraded a Compaq laptop from the factory-installed Vista to Windows XP for this very reason.  With the Aero interface active, the computer's fan ran continuously and usually at maximum speed.  Battery life was ridiculously short.  The translucent look of Aero is a gimmick that isn't worth it, in my opinion.  Nonetheless, good luck in you search for a better video card.


Aero really doesn't take THAT much more power. It takes some, but really all it does is ask the GPU to accelerate the GUI. By setting the power profile to "power saver," that disables transparency while on battery. Honestly, by the time drivers matured, 7 beat XP for battery life thanks to other optimizations.  OSX also uses the GPU for GUI work, and I'm pretty sure "3D" linux interfaces (Gnome3) offload that as well, hence the need for a better GPU. Many laptops just run warm and need the fan all the time. They are just powerful CPUs crammed in a small space. The days of passive cooling are gone, even on 10W Atom netbooks. Also, if you have a late model Pentium 4 or Pentium D, having the fan ramp up is just a way of life. 

In regards to the OP, I suggest an eBay/craigslist hunt. Find yourself an nVidia card 8000 series or later with a good memory buffer size. I picked up an 8800GTS 512mb off eBay for $40 shipped. That card can still play modern games, and it works great in Ubuntu.

---

### Post by OliverHaslam on 2012-04-19
Thanks for the replies guys.

What do we think to these?

[http://www.overclockers.co.uk/showproduct.php?prodid=GX-121-MS&groupid=701&catid=1914&subcat=1833](http://www.overclockers.co.uk/showproduct.php?prodid=GX-121-MS&groupid=701&catid=1914&subcat=1833)

[http://www.overclockers.co.uk/showproduct.php?prodid=GX-140-GW&groupid=701&catid=1914&subcat=1833](http://www.overclockers.co.uk/showproduct.php?prodid=GX-140-GW&groupid=701&catid=1914&subcat=1833)

---

### Post by SeijiSensei on 2012-04-19
The first one has a better processor and more memory, so I'd go with that.

---

### Post by OliverHaslam on 2012-04-19
> **SeijiSensei said:**
> The first one has a better processor and more memory, so I'd go with that.

Went for the 2nd, just because it's fanless. I figure 512MB is plenty.

---

### Post by MonkeyPaw on 2012-04-19
Yeah, 512MB will do. Honestly, both cards are not that different when it comes to performance, and neither will really set the world on fire.

Just as a warning, make sure you have some decent airflow in your case, or maybe point a case fan at it if you can. While it CAN run passively, it will probably last longer for you if it had at least some air movement on it.

---

