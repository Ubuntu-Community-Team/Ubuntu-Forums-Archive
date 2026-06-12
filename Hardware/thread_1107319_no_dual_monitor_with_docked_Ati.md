---
title: "no dual monitor with docked Ati"
date: 2009-03-26
forum: Hardware
---

### Post by fangorious on 2009-03-26
I have an HP nw8240 notebook with an Ati FireGL V5000 Mobility (although it is identified as a Mobility Radeon X700) that I could never configure dual monitors on while docked. I have two HP 1955 digital flat panels attached, one with DVI-I (single link), and one with a VGA-to-DVI-A cable. I'm running 8.04.2 with the Catalyst 9.2 drivers, and have not edited xorg.conf (I've tried in the past but I'm wanting to start from a clean slate). The monitor connected digitally is automatically configured properly, to the native resolution (1280x1024@75). The other monitor (analog connection) shows an OSD message of "signal out of range", and them goes into standby. Just so there's no question that the hardware does what I want it to, dual monitor support with both showing 1280x1024@75 with the same cables works just fine in Windows. 

With the notebook docked the Catalyst Control Center shows 3 displays, with 1 and 2 kind of overlayed. So I assume that this is a result of the VGA port on the being a pass-through of the notebook's display panel. If I click the identify button the digital monitor shows a 3. I've attached a tar file with a couple of screenshots of the Catalyst Control Center and my xorg.conf. It doesn't seem to matter what settings I try in CCC, it either seems to do nothing or apply the settings to display 3, even if I had selected one of the other 2 displays.

---

