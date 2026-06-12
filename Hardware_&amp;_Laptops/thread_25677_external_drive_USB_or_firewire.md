---
title: "external drive: USB or firewire"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by hohllp on 2005-04-10
Hi all,

I am planning to buy a external hard disk (likely western digital SATA), and I would like to know your opinions whether I should go USB 2.0 or firewire. This questions is with respect to both compatability and performance ... the first being more important than the second. I've been seeing that firewire may still pose some problems, but are these cases sporadic, and due to improper configuration, or are there genuine problems with using firewire in linux. I would prefer getting firewire performance sake, but if USB will make my life a whole lot easier I may go with that instead. Thanks for the help. Also is SATA fully supported in linux, or should I just stick with ide. 

Vince


p.s. if I am missing a previous post that explains all this please direct me to it. I tried to look for one but found very little with repect to answering this general question.

---

### Post by mathjazz on 2005-04-10
Notice that in theory, [USB 2.0](http://en.wikipedia.org/wiki/Universal_Serial_Bus) works at 480 Mbit (60 MBytes) per second, whereas [Firewire](http://en.wikipedia.org/wiki/FireWire) only at 400 Mbit (50 MBytes) per second.

But in praxis it's usually  [not that simple](http://www.barefeats.com/usb2.html).

---

### Post by souki on 2005-04-11
I use an external firewire (400) for backups and it works very well
the implementation is the same as USB (via the sbp2 module) and you will see it as a scsi disk
what makes me choose Firewire400 is the hability to use long cable (mine is 6 meters long)

The sensible part is the chipset, mine is an ohci1394 and is very well supported: tested with the integrated firewire on my laptop and on an other laptop with a firewire-pcmcia (same chipset)
I don't know about USB2, but you have to check if your chipset is supported

---

### Post by hohllp on 2005-04-11
Thanks for the help. Looks like I am going to get the Western Digital Caviar SE 200GB, with a Masscool 3.5" USB 2.0 / Firewire External Hard Drive Enclosure.  It's only 10$ more for both connection types, and the enclosure seems to have gotten reviewed well. I think I'll stick with IDE interface for now, since I had trouble finding many SATA enclosures that go to firewire.

Vince

---

