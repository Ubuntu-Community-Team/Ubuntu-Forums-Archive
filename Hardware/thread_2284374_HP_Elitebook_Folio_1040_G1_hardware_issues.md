---
title: "HP Elitebook Folio 1040 G1 hardware issues"
date: 2015-06-29
forum: Hardware
---

### Post by monkley on 2015-06-29
This is as much for reference as a twist for help. 

Ubuntu 14.04 installed without much fuss, although had had to delete the HP_TOOLS partition as the drive already had 4 primary partitions. 

Ubuntu is super snappy but I can live with the touch pad. I guess it's down to drivers but right mouse click via two finger touch is a mess, and as there are no physical mouse buttons, it's unusable for me. Also two finger scroll doesn't work,although you can use the right edge to scroll add a workaround. 

I'm hoping that the drivers get sorted soon as it would be a killer setup otherwise.

---

### Post by Tsahre on 2015-06-29
You can use a driver update tool to fix the driver issues.

---

### Post by Yellow Pasque on 2015-06-30
You need a newer kernel: [https://github.com/torvalds/linux/commit/5715fc764f7753d464dbe094b5ef9cffa6e479a4](https://github.com/torvalds/linux/commit/5715fc764f7753d464dbe094b5ef9cffa6e479a4)
At least 3.18 from my understanding: [https://github.com/torvalds/linux/commit/aa972409951e0675e07918620427517cad5090e0](https://github.com/torvalds/linux/commit/aa972409951e0675e07918620427517cad5090e0)

You can either move to Ubuntu 15.04 or try the linux-lts-vivid kernel in 14.04.

> **Tsahre said:**
> You can use a driver update tool to fix the driver issues.
What tool are you referring to that updates the synaptics kernel module? Does "Additional dDrivers" do that?

---

### Post by monkley on 2015-07-01
> **Temüjin said:**
> You need a newer kernel: [https://github.com/torvalds/linux/commit/5715fc764f7753d464dbe094b5ef9cffa6e479a4](https://github.com/torvalds/linux/commit/5715fc764f7753d464dbe094b5ef9cffa6e479a4)
At least 3.18 from my understanding: [https://github.com/torvalds/linux/commit/aa972409951e0675e07918620427517cad5090e0](https://github.com/torvalds/linux/commit/aa972409951e0675e07918620427517cad5090e0)

You can either move to Ubuntu 15.04 or try the linux-lts-vivid kernel in 14.04.


Thanks! Good to see that forcepad support has been built in already. I'll try it out and report back.

---

### Post by vq1 on 2015-07-01
funny, I have a elitebook 2730 and my trackpad, mouse pointer, left/right click all work but my internal keyboard does not. Best of luck!

---

### Post by monkley on 2015-07-03
Ok, so I've upgraded the kernal to 3.19 and hurrah, two finger scroll is here! Also two finger right click works now, in fact even the "force" feature works which is pretty impressive.
Now I just need pinch to zoom :p

---

