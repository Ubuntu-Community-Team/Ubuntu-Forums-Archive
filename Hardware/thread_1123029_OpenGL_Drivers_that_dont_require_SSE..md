---
title: "OpenGL Drivers that dont require SSE."
date: 2009-04-11
forum: Hardware
---

### Post by MechWarrior001 on 2009-04-11
Hey, me again.

My current system (My GOOD one had a motherboard meltdown) has a AMD Athlon ~1.2gHz (Socket 462/A)
and does not support SSE. However, the Nvidia 177 drivers say SSE is required for OGL Functionality.

Are there any replacement OGL drivers that will allow me to use my Nvidia 7800 GS (AGP 8x)? I dont want to have to use the built-in Via schipset (I cant even play AssaultCube with it, as I max out at 1 FPS on LOWEST settings)

---

### Post by ajmorris on 2009-04-12
> **MechWarrior001 said:**
> Hey, me again.

My current system (My GOOD one had a motherboard meltdown) has a AMD Athlon ~1.2gHz (Socket 462/A)
and does not support SSE. However, the Nvidia 177 drivers say SSE is required for OGL Functionality.

Are there any replacement OGL drivers that will allow me to use my Nvidia 7800 GS (AGP 8x)? I dont want to have to use the built-in Via schipset (I cant even play AssaultCube with it, as I max out at 1 FPS on LOWEST settings)

hi there,
as of the nvidia drivers, version 173.xxx, nVidia decided to make them require SSE. You can simply downgrade your nvidia drivers to an older version. You can play around with driver versions to see which ones dont require SSE. I know for sure the 100.14.19 doesnt need it. To downgrade your drivers, you will have to remove the drivers you have installed from the ubuntu repositories, and download the older versions from upstream.

AJ

---

### Post by MechWarrior001 on 2009-04-12
What do you mean by upstream? are you referring to a earlier version of Ubuntu?

---

### Post by ajmorris on 2009-04-13
> **MechWarrior001 said:**
> What do you mean by upstream? are you referring to a earlier version of Ubuntu?

sorry, by upstream i mean the drivers from the nvidia developers themselves, i.e from [http://nvidia.com](http://nvidia.com)
I meant an earlier version of the nvidia drivers, not ubuntu :)

AJ

---

### Post by MechWarrior001 on 2009-04-13
Ah, thanks. I'm installing nvidia-glx-new (100.XX), which is a Gutsy release, which explains why I'm wasting time downloading all the requirements manually, instead of using terminal.

Do you know of a way to allow Synaptic & Terminal to download packages from previous releases before, you know, Intrepid?

---

### Post by ajmorris on 2009-04-14
> **MechWarrior001 said:**
> Ah, thanks. I'm installing nvidia-glx-new (100.XX), which is a Gutsy release, which explains why I'm wasting time downloading all the requirements manually, instead of using terminal.

Do you know of a way to allow Synaptic & Terminal to download packages from previous releases before, you know, Intrepid?

You aren't able to run multiple repositories for different versions of ubuntu on the same system, e.g the universe repositores for intrepid and jaunty. You *could* switch to older repos via /etc/apt/sources.list and install the necessary packages, then change back to the newer repos, but i strongly advise against doing this, as you will most likely get dependency headaches, and problems afterwards with system libraries etc. Also, every subsequent upgrade, will try to upgrade these older packages, unless you were to blacklist them from being upgraded.. however, tbh the best way would be to either download the nvidia drivers from upstream, and install them against your ubuntu kernel.
With your current method... im not sure why you have that many dependencies on the older versions of the nvidia drivers? if you have the latest version of the nvidia-glx-new package and you install it, then try and run dpkg -i on the older version, it shouldn't realistically have any dependencies, as they should already be installed... Unless the drivers require older versions of the dependencies.

AJ

---

