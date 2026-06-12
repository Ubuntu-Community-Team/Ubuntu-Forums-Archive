---
title: "Hard Disk on a floppy eide"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Tyson D on 2009-08-16
I have a second hard disk sitting in front of me and i was wondering could i attach it through the floppy1 EIDE port/input thing? (please note noobish language)

---

### Post by Whiffle on 2009-08-16
I don't think so, wrong number of pins, probably don't share the same protocol.

---

### Post by earthpigg on 2009-08-16
if the plug fits, plug it in, see if it works. it will cost you nothing. if the plug doesn't fit, dont force it.

ensure your computer is protected from ESD when the case is open, and you have nothing to worry about, nothing to lose.

---

### Post by wojox on 2009-08-16
I think the cable plug is to small but there is usually a second plug on the hard drive cable so you can master/slave the two.

---

### Post by wojox on 2009-08-16
> **earthpigg said:**
> if the plug fits, plug it in, see if it works. it will cost you nothing. if the plug doesn't fit, dont force it.

ensure your computer is protected from ESD when the case is open, and you have nothing to worry about, nothing to lose.

```
sudo apt-get -f install SecondHardDrive
``` :P

---

### Post by presence1960 on 2009-08-16
If you haven't got 2 IDE hard disks already go out and buy a master/slave cable.

---

### Post by Tyson D on 2009-08-16
ok upon closer inspection the floppy1 port is something very different then the eide for the hard disk.

i already have a master/slave cable but the slave is hooked up to my disk drive. Are there alternate ways of hooking up a disk drive or are there master/slave/slave cables? Is it ok or even a good idea to operate without a disk drive?

---

### Post by Mark Phelps on 2009-08-17
> **Tyson D said:**
> ok upon closer inspection the floppy1 port is something very different then the eide for the hard disk.
I'm surprised no one told you this already.

>  Are there alternate ways of hooking up a disk drive or are there master/slave/slave cables? 
No .. there are only two channels, hence, only two connectors on the cable.
> Is it ok or even a good idea to operate without a disk drive?
If you mean hard disk, don't know how you would do that unless you installed entirely to a USB stick.

---

### Post by Tyson D on 2009-08-19
no no no i meant a cd-rom, can i get away with not having one. See I already have amaster/slave cable hooked up to a hard disk and a cdrom. which then i could have both hard disks and no cdrom.

---

### Post by doorknob60 on 2009-08-19
If you don't think you'll want to use your CD drive, go for it. Won't harm anything. I'd consider one of these if I were you though: [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150410%201193212548&name=IDE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150410%201193212548&name=IDE)

Or just get a new SATA hard drive (assuming you have SATA ports)

---

### Post by presence1960 on 2009-08-19
> **doorknob60 said:**
> If you don't think you'll want to use your CD drive, go for it. Won't harm anything. I'd consider one of these if I were you though: [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150410%201193212548&name=IDE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150410%201193212548&name=IDE)

Or just get a new SATA hard drive (assuming you have SATA ports)

If you don't want a CD/DVD drive, make sure you can boot from USB so you can make a bootable USB from the Live Cd iso. You are going to need the function of that if you ever need to do repairs on your installed system or want to create/alter partitions.

Those cards are ok, but I recall a couple of threads where the machine wouldn't boot an OS from one of those, but it would allow access to files. I can't recall if it was a Linux issue or a motherboard issue.

---

