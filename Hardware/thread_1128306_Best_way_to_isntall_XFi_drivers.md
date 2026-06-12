---
title: "Best way to isntall XFi drivers?"
date: 2009-04-17
forum: Hardware
---

### Post by ProbablyX on 2009-04-17
Hello!

I have an X/Fi XtremeGamer card (PCI) and Ive found like 3 different ways to get drivers for it for Ubuntu (Jaunty RC). Either use Creatives official one (do make, make install), Creatives beta ones (with an installer script) or get alsa-drivers and compile them yourself.

I was wondering which way is most likely to work to get an XFi running?

Thanks

---

### Post by ProbablyX on 2009-04-18
I had problems with Fedora before (never worked), that's why I asked.

However; now when Ive returned to (K)Ubuntu I actually got it working :)

Was quite simple!

1. Install kernel headers and build essentials
2. Download the TAR from Creative.com
3. Untar it
4. make
5. sudo make install

KDE detects a new audio device, and KMix is started and wham! Sound :D

---

### Post by misse- on 2009-05-18
Hi,

Please enlighten me as to which drivers to download from creatives site. Do you have a direct link? Are the drivers generic for X-fi products?

I have a freshly installed Jaunty with the following output from lspci -v

03:04.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at bce0 [size=32]
	Memory at daa00000 (64-bit, non-prefetchable) [size=2M]
	Memory at dac00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi


The only tarball I found was from nov 06 I think.. the filename: XFiDrv_Linux_Public_US_1.00.tar.gz

I'll try it out, but if you know any later drivers, please post it here. Prefferably a direct link :)

Regards,
Misse

---

### Post by zapporius on 2009-05-19
> **misse- said:**
> 
The only tarball I found was from nov 06 I think.. the filename: XFiDrv_Linux_Public_US_1.00.tar.gz

I'll try it out, but if you know any later drivers, please post it here. Prefferably a direct link :)

Regards,
Misse

That's the one, I just did it on kubuntu-9.04 and it worked like a charm. KDE switched to it automagically as well.

---

