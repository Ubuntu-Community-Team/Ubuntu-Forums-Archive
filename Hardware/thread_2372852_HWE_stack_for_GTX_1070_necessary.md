---
title: "HWE stack for GTX 1070 necessary?"
date: 2017-09-29
forum: Hardware
---

### Post by onlineguy on 2017-09-29
Hi,

I am about to buy a Nvdia GTX 1070 for my Ubuntu 16.04 desktop. My plan is to use it for Cuda-based calculations (AI / Tensorflow) and some gaming. I know that I will need Nvidia's proprietery drivers for this, but it is necessary to install the hardware enablement stack beforehand as well? Anything else I will need to prepare?

---

### Post by deadflowr on 2017-09-29
If you download Ubuntu from ubuntu.com (and not from ubuntu old-release archive) hwe will be enabled already.
The version from the main Ubuntu website is currently 16.04.3 and hwe is enabled for it.
Only 16.04(.1) does not have hwe enabled, for that you need to go [http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/"))

---

### Post by onlineguy on 2017-09-29
I do know that 16.04.1 does not include the HWE stack. The question is if HWE is actually needed at all (or not).

---

### Post by Yellow Pasque on 2017-09-29
I don't see why you would need it if you're going to use the proprietary blob. When you first boot with the card, you will need to use 'nomodeset' or recovery mode to get the GUI to start.

---

