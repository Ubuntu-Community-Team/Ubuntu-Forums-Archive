---
title: "I don't understand this &quot;Ndiswrapper&quot; thing"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by rondackcpu on 2007-06-04
I seem not to understand this "ndiswrapper" networking thing.  Any enlightenment would be appreciated.  

Here's what's happening:  I have a Dell 5160 laptop, P IV Core Duo, 512 MB, 40 GB hard disk, only Ubuntu 7.04 installed on whole disk, Ndiswrapper from the Ubuntu repository, NetGear WG511v2 (made in Taiwan, with the Marvell chip set) in the PCMCIA slot.  

With Ubuntu 6.10, I can get this to work easily.  The recipe is: 1. "sudo ndiswrapper  -i WG511v2.INF"; 2. "sudo depmod  -a"; 3. "sudo modprobe ndiswrapper"; 4. "sudo ndiswrapper -m"; 5. "sudo gedit  /etc/modules" and add ndiswrapper as a line.  Works like a charm.

With an up-to-date Ubuntu 7.04, I follow the same recipe, but it doesn't work "out of the box."  Some fooling around with "System>Administration>Network", some fooling around with a second "Network Monitor" icon to the panel.  Suddenly it works.  I don't know exactly what I did to make it work.  Even so, the "Network Manager" icons do not display the "five bars symbol" for signal strength.  Only right clicking the icon and selecting "Preferences" puts up a note which reveals the signal level.

All this is an advance from the original install of 7.04 a month ago.  That was even worse, freeze ups, s..l..o..w responses to any input.  The latest updates, while breaking other people's system, have made it possible to make Ndiswrapper to work with my WG511v2.

My other laptop, a Dell 5000e, with a NetGear WG511(v1), works out of the box with the "five bars symbol" indicating network signal strength.

Any ideas, or confirmation of similar results, would make my life simpler.

---

### Post by adampyre on 2007-06-05
I had similar problems until I blacklisted the bcm43xx alternate driver. Edit your blacklist by doing:

sudo nano /etc/modprobe.d/blacklist

Add the line:

blacklist bcm43xx

at the bottom of the file. You can put a comment directly above it for future reference starting with a #.

Restart and hopefully it works for you. Good luck!

---

