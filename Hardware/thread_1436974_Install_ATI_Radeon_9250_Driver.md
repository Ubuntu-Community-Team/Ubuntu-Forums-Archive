---
title: "Install ATI Radeon 9250 Driver"
date: 2010-03-23
forum: Hardware
---

### Post by Thelinuxgeek on 2010-03-23
Hello. I'm a Ubuntu newbie so I don't really know how it all works. My problem is this: I'm using an ATI Radeon 9250, but there are no drivers for it on my PC so I can't use desktop effects! :cry: I don't don't know how or where to install them! Can anyone Help?
 
 
BTW, I'm running ubuntu 9.04

---

### Post by CheAmr on 2010-04-27
I'm having the same problem

---

### Post by Mark Phelps on 2010-04-27
Basically -- NO. 

Why? Because ATI dropped Linux driver support for that card over a year ago.  The last Ubuntu version to work with that card was 8.10.

You are now stuck using the open source drivers -- which are installed by default.  There are no other drivers that will work with that card and current versions of Ubuntu.

Sorry ...

---

### Post by Thelinuxgeek on 2010-04-28
Well. . . that sucks! I've also got a Geforce 8600 GT sitting in my closet but I can't use it right now because it's a PCIe card and I just have a basic PCI motherboard. Guess I'll have to upgrade. . .

---

### Post by Mark Phelps on 2010-04-28
> **Thelinuxgeek said:**
> Well. . . that sucks! I've also got a Geforce 8600 GT sitting in my closet but I can't use it right now because it's a PCIe card and I just have a basic PCI motherboard. Guess I'll have to upgrade. . .

Yes ... it does! (My card is in the same boat as yours even though it's a lot newer!)

However ... you might try a liveCD of 10.04.  The Released version comes out this Thursday and they've (supposedly) improved the open source ATI video drivers.  You may get better results with that version of Ubuntu.

---

### Post by CheAmr on 2010-04-29
oh ..
I hope so , 
Thank you anyway

---

### Post by krazyd on 2010-04-30
This card has accelerated 3D, video etc using the open-source drivers.

If you install Lucid, you'll have desktop-effects without having to do anything.

---

### Post by krazyd on 2010-04-30
> **Mark Phelps said:**
> Why? Because ATI dropped Linux driver support for that card over a year ago.  The last Ubuntu version to work with that card was 8.10.

You are now stuck using the open source drivers -- which are installed by default.  There are no other drivers that will work with that card and current versions of Ubuntu.

AMD didn't "drop support". They just moved support from fglrx to the open source driver. They still employ developers working on the open-source driver full time!

---

