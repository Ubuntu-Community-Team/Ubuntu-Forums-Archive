---
title: "Graphic being processed by cpu, not gpu"
date: 2009-03-16
forum: Hardware
---

### Post by charlie22 on 2009-03-16
I'm running Ubuntu 8.04. For a while now I've suspected that my graphics card hasn't been used to its full ability. To test this I opened up the screen saver chooser and scrolled through various screen savers. Some of them we very "sticky" and did not run in real time. I opened up the System Monitor and noticed that one core on my cpu was idle and the other core was using 100% cpu.

I immediately suspected a driver issue. Going to Applications > Add/Remove I searched for Nvidia and downloaded the "new" nvidia driver. All that did was make some of the more visually appealing screen savers not even load, while the more simple screen savers still ran.

Not only did I not fix the problem I made it worse. Could someone point me the direction to find the right driver, if that is indeed the issue?

Graphics: GeForce 8800 GTS 320 MB 320-bit
CPU: AMD Athlon 64 X2 6000 (3.0 GHz)

---

### Post by charlie22 on 2009-03-16
Update:
I installed Envy. I let it automatically install an Nvidia driver and I restarted the computer. Now it seems that some screen savers are running more smoothly, but others still cause one of my cpu cores to run 100%. I would think with the graphics card that I have that wouldn't be necessary...even if the cpu was needed I also would think it wouldn't need to run at 100% capacity. So I think the problem is still there.

---

### Post by charlie22 on 2009-03-21
any suggestions?

---

### Post by mpsii on 2009-03-21
```
$ sudo apt-get install mesa-utils
$ sudo glxinfo|grep rendering
```

Make sure "Direct Rendering" reads as Yes.

What nVidia card do you have?
```
$ lspci -v
```

---

### Post by charlie22 on 2009-03-22
Direct Rendering is set to Yes

> 02:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Unknown device 0420
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at f5000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0


---

### Post by charlie22 on 2009-03-28
anyone else able to help?

---

### Post by norwoods on 2009-03-28
unless the screensavers use opengl, cuda or vdpau, i doubt they will be gpu accelerated. i doubt the screensavers use opengl, cuda or vdpau.  i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

