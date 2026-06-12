---
title: "video driver problem"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by florus on 2009-10-30
I have just upgraded a Dell laptop with Intel GM965/GL960 integrated video from 9.04 to 9.10.
During the upgrade I had two error messages: 
1) Could not install nvidia-kernel-common subprocess installed pre-removal script returned error exit status 127
2) Error during commit installArchives() failed

During operation I am repeatedly getting the error message:
nvidia-kernel-common: subprocess post-installation script returned error exit status 1

My instinct is to use synaptic to completely remove nvidia-kernel-common, but I would appreciate confirmation from an expert.

---

### Post by florus on 2009-10-30
I cannot find any useful account of error codes in the documentation, just lists which do not seem to cover the right area. Can anyone point me to the appropriate page?

---

### Post by meaje on 2009-10-31
I don't know if you figgured this out or not but you do not have a nVidia video card in your laptop, it is a Intel GM965 onboard video display controller.  This is the driver you need to be installing / configuring not a nVidia controller, unless Dell did something really strange and added a nVidia controller as well.  Could you post the output from lspci -v please.

Hope this helps,
Jeff Means

---

### Post by 3esmit on 2009-10-31
Your video driver is working properly? Resolutions, effects, ect.?

---

### Post by florus on 2009-10-31
> **meaje said:**
> I don't know if you figgured this out or not but you do not have a nVidia video card in your laptop, it is a Intel GM965 onboard video display controller.  This is the driver you need to be installing / configuring not a nVidia controller, unless Dell did something really strange and added a nVidia controller as well.  Could you post the output from lspci -v please.

Hope this helps,
Jeff Means

I have no idea why I have an Nvidia driver; seems weird to me. I think this is the only relevant part of the output: 

lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Device 0227
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Dell Device 0227
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at eff8 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Dell Device 0227
	Flags: bus master, fast devsel, latency 0
	Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

Display has no problems that I can see. Thanks for your help.

---

### Post by 3esmit on 2009-10-31
> **florus said:**
> I have no idea why I have an Nvidia driver; seems weird to me. I think this is the only relevant part of the output: 

lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Dell Device 0227
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Subsystem: Dell Device 0227
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at eff8 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Subsystem: Dell Device 0227
    Flags: bus master, fast devsel, latency 0
    Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

Display has no problems that I can see. Thanks for your help.
Ubuntu comes with "all" (avaliable) drivers. Becouse of this you have it.. But you can unistall it if its coming to troubles to you, and you dont use it.

---

### Post by Bearly Able on 2010-06-23
I have exactly the same problem after upgrading my laptop from 8.04 to 10.04.  I also don't have nvidia graphics.

I've tried using synaptic to remove nvidia-kernel-common, but it fails with the same error message (subprocess installed pre-removal script returned error exit status 127).  

I would just leave it alone, but it returns an error message (subprocess installed post-installation script returned error exit status 1) every time I use synaptic or system update, which is becoming irritating.

Please can anyone tell me how to stop the error messages?

Thank you.

---

### Post by Bearly Able on 2010-07-01
Any suggestions, please?  :confused:

---

