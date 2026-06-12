---
title: "SATA drive wont format correctly???"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Hellstudios on 2009-04-19
Hi, I recently got a 160GB sata HDD that was External, so I decided "hey! I'll take out the enclosure and hook it up to be internal!"  Every thing went fine until I decided to install my OSes on there. so I boot up from my CD drive with ubuntu 8.10, choose to format it to NTFS (I dual boot, you see.) and be on my merry old way, but an error came up, so I try again, and Notice that the drive has disappeared! So I reboot again with my CD drive, try to format it ext2 thinking "screw windows. I'll worry about that later" and the same error comes up and the drive disappears again!

computer specs:
celeron D processor
(I believe) it's an ASUS mobo
1gb RAM
256mb ati radeon xpress video card

The Error:

[img]http://i207.photobucket.com/albums/bb134/hellstudios/error-1.png[/img]



P.S. my computer only recognises the first 149GB of the drive, could this have to do with anything?

---

### Post by Mark Phelps on 2009-04-20
> **Hellstudios said:**
> P.S. my computer only recognises the first 149GB of the drive, could this have to do with anything?

If by your computer, you mean your BIOS screens, then yes -- that has everything to do with it.

To see the entire drive, you will have to either upgrade the BIOS to a newer version (one that can see drives with greater capacity) or buy and install a disk controller card that can do that.  

Either way, this can't be "fixed" in Linux -- it can't see anymore than the BIOS does.

---

### Post by coffeecat on 2009-04-20
Unless the OP means 149GiB ([Gibibytes]("http://en.wikipedia.org/wiki/Gibibyte"))*, which is what Gparted reports capacities in. 149GiB = 159.99 GB ([Gigabytes]("http://en.wikipedia.org/wiki/Gigabyte")), which is what manufacturers quote their capacities in.

For example, on my main machine I have two Samsung SATA drives. sda = 160GB and sdb = 250GB

Gparted reports sda as being 149.05GiB (=160.04GB), and sdb as being 232.88GiB (=250.05GB).

So, both the OP's computer and Ubuntu are probably recognising all the drive after all.

Just a thought. :p

* **Edit:** yes, he/she does. I can see 149.05GiB there (don't forget the 0.05 of a GiB - you never know when you might need it :wink: ), so either the OP has a Samsung drive as well, or has a drive of another make with the same geometry.

A gigabyte (in the strict sense) = 1,000,000,000 bytes.
A gibibyte = 1,073,741,824 bytes.

---

