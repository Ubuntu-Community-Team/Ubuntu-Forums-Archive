---
title: "inexpensive NAS appliance recommendations"
date: 2009-05-24
forum: Hardware
---

### Post by gammb on 2009-05-24
The DLink DNS321 I obtained is very cheap.  Unfortunately it has minimal proc/mem recources and cannot begin to take advantage of it's 10/100/1000 port.  It was slow via CIFS and seems somewhat slower via NFS (ala FunPlug).

Anyone got any recomendations for a 2-SATA-bay NAS under, say, $300; that offers significantly better throughput performance on a Gigabit LAN ?
+Diskless: I already have a pair of 1TB have drives.
+NFS: supported, preferably by design (vs a hack)
Plus: manageable via SSH (as well as HTTP)
Bonus: can run a FireFly (mt-daapd) service

Thanks for any experiences any might share.

---

### Post by vincent orange on 2009-05-24
I don't have any direct experience although with two 1Tb drives are you looking for an enclosure or do you want to build a tiny machine with it? you can buy 2nd hand celerons machines on ebay for £40 all in and then just add the drives. OS software can be anything you like and can boot the whole thing from a 256mb usb pendrive.

you want to use firefly, I'm not quite sure how it works but a quick google indicated that it needs an OS like platform.....this might limit your choice to just a minimal install of ubuntu on a 512mb usb pendrive.

look into
FreeNAS (BSD based)
UnRaid (not entirely free but a solution)
OpenFiler (*nix based)

hope that helps in some way.

---

### Post by gammb on 2009-05-24
Thank you for your suggestion.  I have a 3TB *Tyan-MB + 3ware-Raid + 10x300GB) rackable rig, running CentOS, that I am going to be eBay'ing because I've grown weary of the fan noise.  Getting rid of the rack too.  It's way over the top for a home-office.
I am looking for something small, quiet, and off the shelf.  I am a networking specialist by trade and in my little world, the term "appliance" infers all those things.  My initial post should have been more detailed in that regard.

I am hoping to find some reasonably-priced off-the-shelf appliance that, while not as blazingly fast as the 3TB rid, is distinctly faster than the Dlink appliance I bought to replace it.

...and no, I have no need for 3TB of personal NAS.  It was an adventure.  I'm looking for less adventure, and a quieter office, now.  :-)

---

### Post by vincent orange on 2009-05-25
the hottest thing for small NAS appliance has been the Drobo from Data Robotics. In the UK that thing is priced at 350 Sterling, so that's way over your 300 dollar budget. But it does have Apps that can be installed ontop of it to give you extra functionality.

I think FreeNAS is a good option for you. AFAIK is has all the features you want (except for firefly).

If you want something off the shelf then I  saw these two that might fit your budget. These items are found in the UK, I'm not sure you'll be able to source them but it's a step in the right direction. 

Cisco Network Storage System with 2 Bays (£124)
[http://www.dabs.com/products/cisco-network-storage-system-with-2-bays-4Z4Z.html?refs=4294951313-48940000](http://www.dabs.com/products/cisco-network-storage-system-with-2-bays-4Z4Z.html?refs=4294951313-48940000)

ZyXEL NSA-220 2-Bay SATA Network Storage Enclosure W/ Gigabit LAN & DLNA Media Server - 91-016-006004B (£172)
[http://www.broadbandbuyer.co.uk/Shop/ShopDetail.asp?ProductID=4999](http://www.broadbandbuyer.co.uk/Shop/ShopDetail.asp?ProductID=4999)

I can't comment on either product as I don't own either, but they seem to fit your requirements.

---

