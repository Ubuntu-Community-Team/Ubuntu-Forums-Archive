---
title: "Installing Intel Wireless 3945 driver WITHOUT nvidia?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by jpb39 on 2007-06-20
I have installed 7.04 amd64 on a Vaio FZ11S, which has an NVIDIA 8400M GT GPU and an Intel 3945ABG Wireless adapter. The only way that I can get a functioning display is with the latest NVIDIA driver, which only works once I have removed the nvidia-kernel-common package. Removing the nvidia-kernel package also removes the linux-restricted-modules packages, which I need to install to get the 3945 driver. Reinstalling the nvidia-kernel package leaves me again with no display, until I have removed the package and reinstalled the NVIDIA driver.

Is there any way of enabling the wireless adapter without loading the counterproductive nvidia-kernel package (short of compiling my own driver from the sources at the Intel support site)?

Thanks for any suggestions.

 JPB

---

### Post by Syke on 2007-06-20
Does the open source "nv" driver support the 8400?

---

### Post by jpb39 on 2007-06-20
I must admit that I don't know. I couldn't even start ubuntu on the laptop with any of the installed drivers (from either the i386 or amd64 versions). The X server fails to start and the machine hangs. I eventually loaded the os in text mode with the alternate disk. The installed system again had no display, so I manually installed the recent NVIDIA drivers. Still no joy, until I uninstalled all of the previously installed drivers and reinstalled the NVIDIA one. So if the current nvidia-glx-new does work, I guess the current installer scripts aren't able to recognize the hardware and install it.

 JPB

---

