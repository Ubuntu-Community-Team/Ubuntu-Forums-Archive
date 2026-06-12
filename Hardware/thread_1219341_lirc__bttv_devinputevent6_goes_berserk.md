---
title: "lirc / bttv /dev/input/event6 goes berserk"
date: 2009-07-21
forum: Hardware
---

### Post by akos.maroy on 2009-07-21
I was trying to make my AverMedia TVPhone 98 card's IR receiver work by tring to install lirc according to various online documentation pages - but at the end I ended up with the /dev/input/event6 device that is associated with the IR receiver going berserk - and continously dumping keyboard input on my machine. it's so bad, that even during boot these dummy keyboard events are coming.

the only way I can get rid of this is that I blacklist the bttv module.

this is what I have:

```

# lspci | grep Bt
02:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
# cat /proc/bus/input/devices
...
I: Bus=0001 Vendor=1461 Product=0001 Version=0001
N: Name="bttv IR (card=41)"
P: Phys=pci-0000:02:0d.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:02:0d.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=40fc310 82140000 0 0 0 0 2048000 180 4001 9e0000 0 0 ffc
# cat /dev/input/event6
(an infinite amount of rubbish is coming)

```


this is all despite the fact that the IR remote is not being used - I can even inplug the IR receiver from the card, I still get the bogus input.

I also purged all lirc-related packages, and re-installed the kernel, so that no bogus modules are around that were build by the lirc install process.

how can I stop this madness?

---

