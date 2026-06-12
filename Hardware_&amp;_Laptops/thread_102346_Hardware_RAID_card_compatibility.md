---
title: "Hardware RAID card compatibility"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by rustybutt on 2005-12-11
I'm looking to whip up a simple and cheap RAID filer for my home environment
using Breezy Badger Ubuntu.  I'd like to just pick up a Pentium III box
with about a 10 gig drive and just add a couple more 250 gig drives in a simple
mirror.  The question I have here is does anyone have a good experience with
any of the hardware RAID cards out there and Ubuntu?  I figure I'd get better
performance with RAID 1 and SATA drives than doing a software RAID 1 with
straight ATA IDE drives.

Recommendations?

RustyButt

---

### Post by fabiand on 2005-12-12
Hey,

i've got severall 3ware controllers running under ubuntu 9xxx and 7xxx series. They are working quite well ... also the tool provided by 3ware .. you can check your raid via a ewb interface.

I decided to use ATA not SATA, cause of the costs  ...

- fabiand

---

### Post by WildTangent on 2005-12-12
Many hardware SATA RAID controllers come with drivers for linux. They're likely .rpm files though, so you'll need to use Alien to convert them to .deb

However...finding a card that will work on a normal PCI interface (as opposed to PCI-X, NOT EXPRESS) will be tough. I know they exist, I remember reading about one, but I forgot where. Also, these cards usually come with 8 ports, probably more than you need, and they're very expensive. You're probably better off using a PATA setup.

-Wild

---

