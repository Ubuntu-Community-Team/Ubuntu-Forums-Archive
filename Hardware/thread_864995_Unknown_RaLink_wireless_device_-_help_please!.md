---
title: "Unknown RaLink wireless device - help please!"
date: 2008-07-20
forum: Hardware
---

### Post by mafi01 on 2008-07-20
Hi,

I'm having a lot of trouble getting my wireless adapter working in Ubuntu 8.04. I've looked just about everywhere, but I can't seem to find a proper solution. I should point out though, that I'm a next-to-complete n00b, so bear with me :-)

A sudo lshw gives this output:

*-network UNCLAIMED

                description: Network controller

                product: RaLink

                vendor: RaLink

                physical id: 0

                bus info: pci@0000:08:00.0

                version: 00

                width: 32 bits

                clock: 33MHz

                capabilities: pm msi pciexpress bus_master cap_list

                configuration: latency=0


And lspci gives this:

08:00.0 Network controller: RaLink Unknown device 0781

I'm at a complete loss and hope that someone is able to guide me through the steps.

Thank you,
mafi01

PS 'System > Administration > Hardware Drivers' doesn't find anything relating to networdk drivers.

PPS Looking over my driver settings in Vista (where it works just fine), the driver file is netr28.sys

---

### Post by asgerbg on 2008-08-18
I have the exact same problem. Any help would be greatly appreciated!

---

### Post by silo4321 on 2008-08-22
I have the same card in my computer and got it working using the information I found here [http://ubuntuforums.org/showthread.php?p=5114684](http://ubuntuforums.org/showthread.php?p=5114684) post 41 but i used the new drivers from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) the RT2860 ones. I didn't have to do the steps after the make install step. After all this i had to enable it in the proprietary driver section.

---

