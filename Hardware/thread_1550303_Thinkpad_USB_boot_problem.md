---
title: "Thinkpad USB boot problem"
date: 2010-08-10
forum: Hardware
---

### Post by natgab on 2010-08-10
I have a Thinkpad X40 (no optical drive) that I bought on eBay. It came preinstalled w/ windows XP and works fine. But I am having trouble getting it to boot off a USB stick.

I tried both Universal USB installer and also UNetbootin to install the ubuntu ISOs. They boot into live disc fine on PC in my signature. When I boot on thinkpad, it says boot error. Tried both a SanDisk 8GB & Corsair 32GB USB sticks. Thinkpad has 2 USB 2.0, that work otherwise.

I have it set to boot first to USB-HDD, have also tried using OS menu select after going into bios. Trying to avoid having to buy a USB CD-ROM if possible.

Specs at Thinkpad Linux site:
[http://www.thinkwiki.org/wiki/Category:X40](http://www.thinkwiki.org/wiki/Category:X40)

--I had posted this in install problems, but I think it is more appropriate here.  I will post note for mods to close other thread.

---

### Post by natgab on 2010-08-15
OK, 

I went and asked the Thinkpad forum, [http://forum.thinkpads.com/viewtopic.php?f=3&t=89692](http://forum.thinkpads.com/viewtopic.php?f=3&t=89692) , and checked to see if the laptop had all BIOS updates.  I updated the laptop from BIOS 1.22 to BIOS 2.08.

The BIOS update was not needed, as someone said they were booting from USB using BIOS 1.22.  I was able to keep testing different options and found that I was able to boot using Puppy Linux on a 3rd 256MB flash drive. (since it only requires 128MB) 

So I will have to purchase a 4th flash drive and hope it works with Ubuntu.  

[COLOR="Red"]Update:[/COLOR] The new flash drive worked, I was able to load Xubuntu 9.04 (updated to 9.10) since 10.04 boots to a black screen.  And the alternate install CD will not work as a USB flash drive.

---

