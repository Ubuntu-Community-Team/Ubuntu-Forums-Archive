---
title: "Which PCI WiFi card manufacturer is deserving of my cash?"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by kiwifish on 2006-03-18
Hi all.

I currently have a 3Com USB wifi adapter that i've been using in breezy under ndiswrapper- but it's a bit flaky, and there's no chance of it working under amd64 (which i'm planning on trying out). I have a chance to sell off that adapter to a windows using friend, so i'm going to buy a new PCI wifi card.

Are there any manufacturers that have been good to the linux community and built stable 32/64 bit drivers? or even better released specifications so GPL drivers can be made?

Failing those, can anyone recommend a wifi pci card that will work on an amd64 kernel with the minimum of hassle?

Thanks!

EDIT: I just found [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) - driver source code! that looks promising! does it?

---

### Post by Steve1961 on 2006-03-18
[QUOTE=kiwifish]Hi all.

I currently have a 3Com USB wifi adapter that i've been using in breezy under ndiswrapper- but it's a bit flaky, and there's no chance of it working under amd64 (which i'm planning on trying out). I have a chance to sell off that adapter to a windows using friend, so i'm going to buy a new PCI wifi card.

Are there any manufacturers that have been good to the linux community and built stable 32/64 bit drivers? or even better released specifications so GPL drivers can be made?

Failing those, can anyone recommend a wifi pci card that will work on an amd64 kernel with the minimum of hassle?

Thanks!

EDIT: I just found [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) - driver source code! that looks promising! does it?[/QUOTE]

I've had a lot of success with ralink cards, although I've only used them with 32bit distros.  The Belkin F5D7000(UK) v3 works well, but a full list of cards with this chipset can be found [here.]("http://ralink.rapla.net/")

---

### Post by steve.horsley on 2006-03-18
I just plugged a Foxcomm WLL-3350 in, and it "just worked". That is, after I activated it and got the wep key right. To be fair, this was in Dapper so I can't guarantee it will work with Breezy. The chipset is the RA2500, and I understand that the driver code itself is open source. It was delightfully easy, and the fact that the drivers are open means they really deserver the money, although the foxcomm card is very cheap anyway.

Here is the source where I read the driver was open source:
[http://networkned.co.uk/Wireless.php](http://networkned.co.uk/Wireless.php)

---

