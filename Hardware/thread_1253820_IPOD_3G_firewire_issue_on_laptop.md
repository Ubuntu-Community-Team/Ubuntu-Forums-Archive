---
title: "IPOD 3G firewire issue on laptop"
date: 2009-08-30
forum: Hardware
---

### Post by jdunn on 2009-08-30
I have an IPOD 3G formatted back in 2006 with FAT32.  It can only be charged through a Firewire but it supposedly will sync through firewire or USB.  My laptop computer only has a 4-wire firewire connector (without Vcc).  To remedy this, I have a 6-pin to 4-pin firewire adapter but the laptop still can't provide power to the Ipod.  

Here is the problem:  When I make a data connection with the Ipod, it expects power from the firewire cable.  Otherwise, the Ipod assumes its battery is low and shuts down after about 2-3 minutes.

The music on my IPOD is very valuable (worth more than the IPOD itself) so, I need some ideas on how to copy the music from the IPOD to my laptop.  Here are two ideas I've come up with so far:

1) buy two cheap Ipod dock-to-firewire cables and splice them together such that the IPOD is charged from my Apple firewire AC adapter while data syncs from the computer at the same time.  In theory this should work but its messy.

2)  buy a pcmcia 2-port firewire (6-wire x 2) card from Tiger Direct for $15 so I can data sync and power the IPOD directly from my laptop.  This solution is clean but it may not work without linux drivers and I'm not sure what the status is for drivers on this product.  It supposedly works out-of-the-box on M$ Windows and MAC.  No mention for Linux.  Note:  also I'm not sure it will power the IPOD, even though its 6-wire.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=998911&CatId=510]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=998911&CatId=510")

---

### Post by jdunn on 2009-08-30
Well, it looks like the cardbus/pcmcia option won't work.  Firewire provides approx 24V to power IPOD and there's just no way to get that from pcmcia/cardbus.  Sabrent makes no mention of this.  Neither does the $10 Compaq firewire port cardbus card specs.  Some of the more expensive cards like the Startech have a connector so you can provide 24V to firewire externally through an adapter...but this is more than I'm willing to pay:  $40 for startech card + at least $10-20 for adapter.

---

