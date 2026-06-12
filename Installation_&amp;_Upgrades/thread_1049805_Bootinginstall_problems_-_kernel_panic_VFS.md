---
title: "Booting/install problems - kernel panic VFS"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by agamotto on 2009-01-24
Hallo all, I recently put together a lunchbox to move up into the dual/quad core territory, and have been having a hell of a day with it.

Motherboard is an ASUS M2N68-VM which POSTS fine, with 2Gb of DDR2 memory.  Cpu is Athlon 64 AM2 5600 running ~2.7Ghz.  The BIOS detects both the IDE hd and dvd drive fine, but when it comes to running/booting anthing I keep getting errors like the following:

[00.004000] Aperture beyond 4GB.  Ignoring.
[00.0011680] ACPI: Aborted because invalid compressed format (err=1)
[00.0020001] ..MP-BIOS Bug:  8254 Timer not connected to IO-APIC
[00.587405] Invalid compressed format (err=1)
[00.589132] Kernel panic - Not syncing: VFS: Unable to mount root fs on unknown block (8,1)

I have tried a Mythbuntu 64-bit live cd, the alternate cd, a Mythdora 64bit cd, Ubuntu 8.10 64-bit cd, and Knoppix live cd.  Knoppix will come up, but it doesn't help me much, as this is going to be a Myth box of some flavor, once I can find something that will boot and install.  With all of the other discs, I get to the 'click install' part, then stuff moves/noises a bit, and some variation on the above pops up.  I never get to partition/boot/live environment.  I tried turning off all ACPI stuff in the motherboard settings, but nothing changes that I can see.


Help?

Of all the idiot things that can go wrong with a motherboard... both the SATA and the IDE cable were toast from the start.  I tried different cables as a joke, and magically, things started to work!

grrrrrr

---

### Post by tommcd on 2009-01-24
Can you boot the live CD and post your /boot/grub/menu.lst from the Ubuntu install on the hard drive? It looks like grub may not be finding the root partition.

Are you running the IDE hard drive and an IDE DVD drive on the same IDE channel? If you are that may be a problem. If you are, then set the hard drive to master and the dvd to slave. I am asking this because your motherboard only seems to have 1 IDE channel:
[http://www.asus.com/products.aspx?modelmenu=2&model=2446&l1=3&l2=149&l3=626&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2446&l1=3&l2=149&l3=626&l4=0)
For what it's worth, at least 1 guy says Mythbuntu 8.10 works on this mobo in the newegg reviews:
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813131355](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813131355)

---

### Post by agamotto on 2009-01-25
> **tommcd said:**
> Can you boot the live CD and post your /boot/grub/menu.lst from the Ubuntu install on the hard drive? It looks like grub may not be finding the root partition.

Are you running the IDE hard drive and an IDE DVD drive on the same IDE channel? If you are that may be a problem. If you are, then set the hard drive to master and the dvd to slave. I am asking this because your motherboard only seems to have 1 IDE channel:
[http://www.asus.com/products.aspx?modelmenu=2&model=2446&l1=3&l2=149&l3=626&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2446&l1=3&l2=149&l3=626&l4=0)
For what it's worth, at least 1 guy says Mythbuntu 8.10 works on this mobo in the newegg reviews:
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813131355](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813131355)


There is no install on the hd... I never get that far.  The manual states that the IDE port supports two devices, and hdd is set as master, with dvd as slave.  Confirmed in BIOS.  

I am glad someone is having luck... it keeps me from thinking I am hopeless!  I will try reformatting the hd with Knoppix and see what happens.  Hell, at this point, it can't hurt...

---

### Post by tommcd on 2009-01-25
I think using the hard drive and the dvd drive on the same IDE channel may be the problem. Can you can get a sata hard drive? If so, set the dvd drive to master on the IDE channel and install to the sata hard drive.

---

