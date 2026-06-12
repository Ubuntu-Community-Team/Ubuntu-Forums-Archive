---
title: "Am I crazy? Ultimate Linux wifi/ethernet router idea ..."
date: 2009-02-01
forum: Hardware
---

### Post by slavik on 2009-02-01
b43 has gotten really good. (I have an older compaq laptop that has a bcom chipset).

So, I was thinking (since I don't have a wifi router), for about 300USD, build an el cheapo neato system from parts from newegg and set it up as a monster wifi router.

The idea behind this is:
- wifi/ethernet router (with named, dhcpd, routed, etc.)
- LAMP stack (substitute P with your favorite web language)
- file/media server (sshfs/nfs/samba)
- VPN point

Think Linksys with DD-WRT on steroids, yet not a high end server. It can also allow to serve content from an external USB devices and even eSata devices if it's possible to turn a sata port into an eSata port (are they the same?)

Here's the part list if anyone is interested (all from newegg) totaling just under 300USD (I have a spare HDD to use):
```

Qty.	Product Description	Savings	Total Price

1	G.SKILL 2GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Desktop Memory
Item #:N82E16820231203
Return Policy:*Limited Non-Refundable 30-Day Return Policy		$17.99

1	ASUS WL-138g V2 PCI Wireless Adapter
Item #:N82E16833320022
Return Policy:*Limited 30-Day Return Policy		$23.99

1	APEX MI-008 Black Computer Case
Item #:N82E16811154091
Return Policy:*Standard Return Policy		$55.99

1	JetWay JNC62K Mini ITX AMD Motherboard
Item #: N82E16813153114
Return Policy:*Limited 30-Day Return Policy
AMD Athlon X2 4850e 2.5GHz Socket AM2 45W Dual-Core Processor
Item #: N82E16819103255
Return Policy:*Processors (CPUs) Return Policy	-$20.00*Combo	[s]$211.98[/s]
                                                               $191.98

[SIZE="5"]**Grand Total:			$289.90**[/SIZE]

```

Maybe write up some web interface to manage this thing and have a new project?

---

### Post by Mooie on 2009-02-01
why not an intel processor?  The e8400 should be faster than that amd, and its $20 less.

---

### Post by slavik on 2009-02-01
motherboard choice drove the decision mostly. the motherboard is a dual gigabit mini-ITX form factor. the CPU is dual core and more than enough for this purpose IMO.

---

### Post by mozetti on 2009-02-01
Why not install DD-WRT on a x86 machine? They have a build specifically for this use.

---

### Post by slavik on 2009-02-02
err, that's what I am building ... an x86 machine ... but I haven't see what the DD-WRT interface looks like so I cannot say what it is capable of.

---

