---
title: "Is a Dell 1900 Ok for a used Home Server?"
date: 2012-12-11
forum: Hardware
---

### Post by itpro007ca on 2012-12-11
I'm toying whether to buy this Dell 1900 Tower Server on Ebay and I see it is 2003 made,from my searching LOUD and I'm wondering whether to replace my Biostar NF61S motherboard,nvidia geforce 6100,2gb ram,160 gb sata drive and LG dvdrw,already almost at 2gb ram,with this monster!?

	
Dell PowerEdge 1900 -Xeon E5335 QC@2GHz,16GB DDR2 ECC,2x300GB SAS HD, LTO2,DVDR^:

[http://www.ebay.ca/itm/Dell-PowerEdge-1900-Xeon-E5335-QC-2GHz-16GB-DDR2-ECC-2x300GB-SAS-HD-LTO2-DVDR?item=271116431337&cmd=ViewItem&_trksid=p5197.m7&_trkparms=algo%3DLVI%26itu%3DUCI%26otn%3D5%26po%3DLVI%26ps%3D63%26clkid%3D4089994948013689858]("http://www.ebay.ca/itm/Dell-PowerEdge-1900-Xeon-E5335-QC-2GHz-16GB-DDR2-ECC-2x300GB-SAS-HD-LTO2-DVDR?item=271116431337&cmd=ViewItem&_trksid=p5197.m7&_trkparms=algo%3DLVI%26itu%3DUCI%26otn%3D5%26po%3DLVI%26ps%3D63%26clkid%3D4089994948013689858")

Advice,please and thanks.

---

### Post by ahallubuntu on 2012-12-11
Yeah, loud is bad.  For a "home server" a conventional desktop tower is probably sufficient.  Personally, I'd just build a new Sandy Bridge or Ivy Bridge box.  A Celeron Dual Core CPU Sandy Bridge would be just fine and run really cool and low power but have plenty of horsepower for a "home server."  There are deals on motherboards all the time, RAM is cheap.  You can get a Celeron G530 with fan for about $45 USD shipped.

Otherwise, minimum I'd want a Core 2 Duo - era CPU.  Avoid Pentium 4 class, too power hungry and inefficient.

---

### Post by itpro007ca on 2012-12-11
> **ahallubuntu said:**
> Yeah, loud is bad.  For a "home server" a conventional desktop tower is probably sufficient.  Personally, I'd just build a new Sandy Bridge or Ivy Bridge box.  A Celeron Dual Core CPU Sandy Bridge would be just fine and run really cool and low power but have plenty of horsepower for a "home server."  There are deals on motherboards all the time, RAM is cheap.  You can get a Celeron G530 with fan for about $45 USD shipped.

Otherwise, minimum I'd want a Core 2 Duo - era CPU.  Avoid Pentium 4 class, too power hungry and inefficient.

*************************
Thanks for the reply.

I've held off for now.I'll see if it gets relisted,then research some more and see.Need more time to research.

"Motherboard."

That's another route I'm looking at.

I note I can get an Asrock motherboard that's good for AM2 and DDR2(which is what I have now:AMD64x2,4 Ghz,2GB 667 Mhz DDR2),and AM3,AM3+,DDR3,thereby enabling me to use what I have now and move up when ready,ie: 4 GB ram

Besides,I read those Dell Servers with their RAID cards,can be tough to set up,but,note,a lot of Linuxers,esp. Ubuntuers,using the Dell 1900,so it must do something right.

Tnx again!

---

### Post by tgalati4 on 2012-12-11
Those older Dell servers are good for experimenting with things like:

RAID
Xen and virtual machines
Private cloud services

But yes, they are loud and power hungry.  My Dell 1750 rack servers (2 dual Xeons) burns 240 watts and it's 7 fans (spinning at 6700 rpm) sounds like a jet taking off.  I built a rack in my garage and I use wake-on-lan to wake them when I need to compile something or start a service.

For an in-home file and media server, there are better solutions, but the hands-on factor of this tossed off equipment (that was $5,000 when new) is tempting.

For my 24/7 file server and media server, I use a Pentium I whitebox overclocked to 277 MHz and a few TB of storage using ZFS and [http://freenas.org](http://freenas.org).  Burns 35 watts and the drives spin down so it's pretty quiet.

---

### Post by ahallubuntu on 2012-12-11
> **tgalati4 said:**
> For my 24/7 file server and media server, I use a Pentium I whitebox overclocked to 277 MHz and a few TB of storage using ZFS and [http://freenas.org](http://freenas.org).  Burns 35 watts and the drives spin down so it's pretty quiet.

It's nice to recycle old hardware when you can, but of course a Pentium I will be severely limited (can't add much RAM, probably can't access SATA drives, etc.).  My recent Sandy Bridge/Celeron  build (little SSD for a hard drive) consumes about 20 watts at idle but still has plenty of CPU power when I occasionally need it.

---

### Post by tgalati4 on 2012-12-11
256MB of RAM and a SATA card takes care of that.

---

