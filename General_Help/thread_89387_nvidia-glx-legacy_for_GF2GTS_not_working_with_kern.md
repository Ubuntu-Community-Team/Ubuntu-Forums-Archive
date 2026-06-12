---
title: "nvidia-glx-legacy for GF2GTS not working with kernel 686 ?"
date: 2005-11-12
forum: General Help
---

### Post by logan77 on 2005-11-12
Hi. The problem is :after replacing GF4200 with GF2GTS on Ubuntu 5.10, kernel 2.6.12-9-686 #1 with nvidia-glx driver i got this : 

(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:03:12 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) The NVIDIA GeForce2 GTS/GeForce2 Pro GPU installed in this
(WW)      system is supported through the NVIDIA Legacy drivers.
(WW)      Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
(WW)      more information.  The 1.0-7667 NVIDIA driver will ignore
(WW)      this GPU.  Continuing probe... 
(EE) No devices detected.

So i went to Synaptic to remove nvidia-glx, install nvidia-glx-legacy, which triggered installing of ... linux-restricted-modules-2.6.12-9-386-nvidia-legacy  (not the 686 version), and i got this : 

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

and sth like "/lib/modules/2.6.12-9-686/volatile/nvidia.ko there is no such device" or similar. But when i manually navigate to this volatile dir i see there is nvidia.ko (for 686 of cos). SO what's wrong ? Does it mean i can't have nvidia-glx-legacy driver with my 686 kernel ? Should i compile it for myself ?

---

