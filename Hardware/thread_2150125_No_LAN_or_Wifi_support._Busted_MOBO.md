---
title: "No LAN or Wifi support. Busted MOBO?"
date: 2013-05-31
forum: Hardware
---

### Post by Ruashiasim on 2013-05-31
New to the Board with a new build from older parts:

[h=1][FONT=arial][SIZE=2]DFI LANPARTY UT NF590 SLI-M2R/G AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard
[/SIZE][/FONT]Athlon 5600x2, 4 gigs ram, 550w psu, Gigabyte 9800gt based card, and wifi pci card[/h]
Been fooling with this motherboard for a while now, had it running windows 7 but would never get online, tried a fresh install of Ubuntu and in either ethernet socket Ubunto does not detect a cat5 cable (which works on my other build and my ps3) no wifi either. I can't figure out how to determine if Ubuntu even sees that a Wifi card is installed but it definitely isn't picking up my open network. I'm thinking at this point that some part of the board is fried and not working right. Ubuntu should automatically work with a cable or a wifi card right?  everything else seems to work fine but I really can't do much to tell not online. thanks for any help.

---

### Post by Ruashiasim on 2013-05-31
It does appear to say "no network devices detected" under the network icon at the top right of the desktop so I'm guessing it doesn't even see the wifi card is there

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by Ruashiasim on 2013-05-31
*-network UNCLAIMED
     description: network controller
     product ACX 111 54mbps wireless interface
     vendor: texas instruments
     physical id: 6
     bus info: pci@0000:02:06.0
     version: 00
     width: 32 bits
     clock: 33Mhz
     compatibilities: pm bus_master cap_list
     configuration: latency=0
     resources: memory:fdffc000-fdffdfff memory:fdfc0000-fdfdffff

---

### Post by Yellow Pasque on 2013-05-31
[http://sourceforge.net/p/acx100/acx-mac80211/ci/master/tree/INSTALL](http://sourceforge.net/p/acx100/acx-mac80211/ci/master/tree/INSTALL) (follow the instructions for dkms, and make sure you have dkms installed)
[http://sourceforge.net/p/acx100/acx-mac80211/ci/master/tarball](http://sourceforge.net/p/acx100/acx-mac80211/ci/master/tarball)

---

