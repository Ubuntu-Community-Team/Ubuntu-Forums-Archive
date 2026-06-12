---
title: "10GBASE-T or 2.5GBBASE-T Network Work With Ubuntu 10.04"
date: 2020-09-22
forum: Hardware
---

### Post by supanatral2 on 2020-09-22
I have a system that runs a very specialized piece of equipment so I'm not able to upgrade the system to a modern day version of Ubuntu sadly.

I push a lot of data through the network to this system but sadly the fact that it's running an old version of Ubuntu doesn't help. I would love to have 10GBASE-T on this system but I'd be more than happy if I could even get 2.5GBase-T to work on it.

Any suggestions?

---

### Post by TheFu on 2020-09-22
10G equipment would be better supported than 2.5Gbps because data centers have had it since 2008-ish.  2.5Gbps seems to be a home/consumer compromised solution.

But you'll need to find 10 Gbps NICs from that era and find drivers from then.  I wouldn't want to be you.  I had a job where I'd have to hunt down 25 yr old hardware to replace systems that had failed.  When the used hardware market couldn't provide replacements anymore, our clients weren't happy - to them any change was bad.  OTOH, after a few months of pain and being forced to lose everything or switch to newer tech, about 80% would move to the newer stuff, if we could make it available in their locations.  20% would lose their businesses. They were just too specialized.

In general, you'll find that people can't help here with unsupported releases. Sorry.  I miss 10.04. To me, it was the finest Linux release of all time. It felt like "linux" and didn't have any surprises. Every release since then has changed something major in a way that caused problems.  New isn't always better, but such is software in our world today.

As for solutions, a few thoughts:

Get new servers and put 10.04 into a KVM+libvirt VM. The new servers would easily support 10Gbps current generation equipment and the virtio drivers from that time should support more than 10 Gbps.  I routinely see 25 Gbps between different VM guests on the same system here.  The hardware would be abstracted away from the VM.  You could had as many bonded virtio NICs to the VM as needed. More than any single NIC would support. Plus, 10.04 on modern hardware inside a VM would fly.
Get on ebay, find 10Gbps NICs from 2010 that had good Linux support and that you can find drivers.  That is probably only from HP, IBM, Dell, and Intel.  Actually, you may be forced to use sc fibre connections from that period.  I bought lots of 10 Gbps NICs back then, but not for PC servers. My job then was specifying Unix Servers (Mainly AIX/HP-UX/Solaris). Sorry.

---

