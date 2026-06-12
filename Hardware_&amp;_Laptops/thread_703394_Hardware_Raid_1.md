---
title: "Hardware Raid 1"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by justtech on 2008-02-21
hmmm... did a lot of searching and I guess there aren't enough people messing with RAID to have a solid tutorial.  Not to mention, this is my first time so I am still incredibly new to the whole process.

Here is what I have... ASUS P5E WS Professional Motherboard, Intel Quad 6600 Processor, 4 Gigs of Ram, 4 hard drives (160gb Primary OS drive, 300 gb Temporary old drive until I get all info off of it, and two 500 gb drives set up in RAID 1 with my motherboard).

Problem:  I need to get Gusty to recognize the RAID setup that I have with the 2 500gb HDDs.  As of now, I am only getting 2 individual 500gb drives formated in ext3.  Isn't it supposed to show up as 1 drive?  When I write something to drive /dev/sdc it does not duplicate it onto /dev/sdd.  Anyone know what I am doing wrong?

---

### Post by mrsteveman1 on 2008-02-21
Hardware raid should isolate any differences from the OS, you shouldn't actually be seeing 2 drives at all.

For instance, if you were using an addon raid card, you would configure that card with a special application in windows/dos/linux, and after this point the card only exposes one drive, doing all the backend stuff itself on the card.

Do you know what chipset is on the motherboard? It might just be a softraid chip, which is in effect software raid with boot support.

---

### Post by justtech on 2008-02-21
It is the ICH9R chipset.  Which I will now start a new search on how to set it up in raid with that format.  I guess it through me off when I was able to set it all up with RAID 1 before I ever got to the OS.  Does that mean I can set them all back to IDE?  Does that mean that I will be using a "fakeraid" or "software raid"?  Any suggestions on which path to take from here?

---

### Post by njparton on 2008-02-21
You're using onboard raid which is software raid not hardware raid as your thread title suggests.

For hardware you need to buy a PCI or PCIE card from 3ware, highpoint etc and for true hardware raid they're around £100 or $200 US+.  The cheaper cards are still software and rely on your CPU to do the work.

I use a 3ware raid card which has drivers built into the kernel.  I can recommend this approach if you can afford it.

---

### Post by justtech on 2008-02-21
Sorry about the mis-title of the thread.  As I said, I am new to the RAID world.  I'm used to having external HDDs where I have to manually back it all up.  Thank you for your reply.

---

### Post by mrsteveman1 on 2008-02-21
I would like to second the 3ware recommendation, they are good cards with good support in linux, and they are true hardware raid cards, the card itself has an embedded processor on it which takes care of all the backend raid stuff, while the OS only sees one device and thus is almost completely isolated from any raid issues.

There is another option as well, you can use the linux mdraid setup which work fairly well for backend storage though im not familiar with booting from an mdraid array.

---

### Post by justtech on 2008-02-21
At Newegg, this is the one that I found that claimed to be hardware supported ([http://www.newegg.com/Product/Product.aspx?Item=N82E16816116041]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116041")).
  Is this what you reccomend?

---

### Post by mrsteveman1 on 2008-02-21
If your computer has an open 1 lane PCIE slot, and all you want is raid 0 on 2 sata disks, that would work fine.

Theres also this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16816116042]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116042")

which supports the higher raid levels and 4 disks, but it requires a free 4+ lane PCIE slot

---

### Post by justtech on 2008-02-21
Awesome, Thank you both for you help and time.

---

