---
title: "Installing ndiswrapper"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by augereffect on 2005-03-13
I've been trying to set up a wireless card, and someone recommended ndiswrapper.  I have no internet connection on that computer at all, but I downloaded the file and transfered it via floppy.  I can't figure out how to open it in synaptic, and I can't find any other way.

Could someone explain to me how to do this in a foolproof manner?

Thanks

---

### Post by bcorcoran on 2005-03-13
you'll need to find a way to at least temporarily connect that computer to the net... because the most foolproof way to install ndiswrapper is via synaptic (in my experiences anyway) and synaptic has it as an available package... 

if you're a linux noob like myself, then you'll not want to install ndiswrapper manually...

another note: ndiswrapper uses the windows drivers to make the wireless card work- so you must at least have an uncompressed driver on a cd or floppy in order to install your wireless card

once you have it installed though, do this:

$ sudo ndiswrapper -i /path/to/drivername.inf

$ ndiswrapper -l
(this command will list the driver you just installed, and whether or not it thinks that the hardware is present--if it is present, the driver is correctly installed

$ sudo ndiswrapper -m
(adds ndiswrapper to modprobe so that it loads on boot)

then you'll want to reboot, and after rebooting, open network-admin and configure your wireless

hope this helps.

---

### Post by wbeck85 on 2005-03-14
as opposed to rebooting, you could just type
#modprobe ndiswrapper
but do

which will load ndiswrapper rightaway

rebooting is icky

#ndiswrapper -m as well so if you do reboot, it will load.

---

