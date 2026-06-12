---
title: "Using cpuburn and hardware monitor from live CD"
date: 2011-03-15
forum: Hardware
---

### Post by Keith_Beef on 2011-03-15
I'm trying to sort out an overheating problem that I have when ripping DVDs in Ubuntu 10.10. I didn't have this problem in 9.04, so I want to boot 9.04 from a live CD and use cpuburn to simulate the ripping load.

So, I booted the live CD, used synaptic to install the sensors to read cpu core temperatures. I ran sensors-detect, did modprobe to load the required kernel modules, and now sensors gives me readings from the i2c bus.

I the hardware monitor, but it does not show up in the list of applets when I try to add it to the panel. Is this some quirk of the live 9.04?

K.

---

