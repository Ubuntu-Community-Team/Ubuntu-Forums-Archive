---
title: "New system build, opinions needed."
date: 2010-04-03
forum: Hardware
---

### Post by wadam on 2010-04-03
Hello everybody --

I just ordered the components for a new system build, and now, before it ships, I thought that I would run the configuration by this forum and see if I can't get some opinions as to whether I'm in for any compatibility headaches.  Specs are as follows:

Core i5-750 CPU
Gigabyte GA-H55M-USB3 Motherboard
PNY GeForce 250 Video Card
ASUS PCE-N13 PCI-e 802.11n wireless adapter
Lite-On SATA CD/DVD Burner
1TB Western Digital Caviar Black Hard Drive
8gb RAM

Specifically, I'm a little bit worried about the motherboard.  Reading through the forums, I've seen some (relatively non-specific) mentions of problems with lock-ups installing and running both Karmic and Lucid. Is this something I should be concerned about?  Should I cancel the motherboard order and go with something else?  If so, any suggestions as to alternate motherboards in the same price-range that offer 1394a and USB3?

Thanks ahead of time!

---

### Post by Naitsirhc Hsem on 2010-04-03
Are you sure you need that much ram? I have three gigs and I only use 300mb on average.  are you a gamer or use vbox?

---

### Post by wadam on 2010-04-03
> **Naitsirhc Hsem said:**
> Are you sure you need that much ram? I have three gigs and I only use 300mb on average.  are you a gamer or use vbox?

I'm pretty much decided on the RAM.  I will be using vbox.  But more pressing, I do a lot of photo editing.  I don't know what the memory needs are for bibble / GIMP.  But I'll probably be dual booting to use the Adobe CS4 Suite, which benefits from throwing as much memory at it as possible.

---

### Post by A9010 on 2010-06-06
> **wadam said:**
> 

Specifically, I'm a little bit worried about the motherboard.  Reading through the forums, I've seen some (relatively non-specific) mentions of problems with lock-ups installing and running both Karmic and Lucid. Is this something I should be concerned about?  Should I cancel the motherboard order and go with something else?  If so, any suggestions as to alternate motherboards in the same price-range that offer 1394a and USB3?

Thanks ahead of time!


hello !  i want to know if you already have that motherboard on ubuntu ?  I'll buy it, but i am searching if i will have problems with any drivers...or something else =)

cheers!

---

### Post by A9010 on 2010-06-06
> **wadam said:**
> 

Specifically, I'm a little bit worried about the motherboard.  Reading through the forums, I've seen some (relatively non-specific) mentions of problems with lock-ups installing and running both Karmic and Lucid. Is this something I should be concerned about?  Should I cancel the motherboard order and go with something else?  If so, any suggestions as to alternate motherboards in the same price-range that offer 1394a and USB3?

Thanks ahead of time!


hello !  i want to know if you already have that motherboard on ubuntu ?  I'll buy it, but i am searching if i will have problems with any drivers...or something else =)

cheers!

---

### Post by wadam on 2010-06-07
A9010 --  I did buy that motherboard.  And I like it very much, save for two problems:  1)  the built in ethernet seems to have quit on me.  And 2) because of the USB3, Linux won't go to sleep.  The former isn't a huge deal, as I have a wireless card that works just fine.  And the later is not specific just to this board.  And it is solvable, though it is annoying.  You have to unload the xhci module before putting the computer to sleep.  Apparently, there should be a fix for this in the kernel sometime soon.  But I wouldn't hold my breath.

Overall, the board isn't bad.  But I would recommend updating to the latest BIOS when you get it.

---

