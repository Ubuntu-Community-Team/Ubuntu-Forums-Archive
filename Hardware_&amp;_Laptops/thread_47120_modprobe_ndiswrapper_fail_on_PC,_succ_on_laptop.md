---
title: "modprobe ndiswrapper: fail on PC, succ on laptop"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by blazko on 2005-07-07
Hello together,

I was delighted to see that Ubuntu comes with ndiswrapper support for my Marvell based WLAN card. However, a modprobe of the ndiswrapper module for the Ubuntu 2.6.10 kernel causes an "Operation not permitted" error. When I do so with insmod, I get "Unknown symbols" - strange, the module is according to the kernel version.

Note that this is everything from the Hoary CD, I have not taken anything from the web so far (am offline with it...) nor from an USB stick or so.

Does anyone know why this error is caused? Strange is, that on my laptop the module can be loaded. The main difference is:

- Laptop: Intel PIII with no WLAN card and no firmware imported: success
- PC: AMD32 with WLAN card and firmware imported: fail

All Ubuntus are installed using the same CD.
The same firmware is working very fine with a parallel installed Debian sid on the same box, so i guess that the formware is okay. Btw.: I think that firmware and ndiswrapper module have no interference at this point; think it's hotplugs job.

Any ideas???

Thanks and greetings,

Timo

---

### Post by varunus on 2005-07-07
I know this is a basic question, but did you type "sudo" before the modprobe?  It won't be permitted if you're just a user and not root...

What version of ndiswrapper are you using with debian sid?

---

### Post by blazko on 2005-07-07
Hello varunus,

I did so with a previous su, so am logged in as root. On Sid, I used most actual release (1.2?).

On Ubuntu, I installed ndiswrapper-utils via Synaptic from the Hoary CD, there ist was labeled 1.0/1.2 (combination???).

Thanks and greetings,
Timo

---

### Post by blazko on 2005-07-09
Rehi,

Sorry for the late reply. just wanted to say that it worked with the actual Sourceforge version (i.e. manual download and install from source).
However, it seems to have a dependency on my home folder?!?! If I replace my home folder with an older one on another partition, ndiswrapper fails to load (much HEX stuff in exception...). Does anyone have an idea? Normally it has only dependencies to /etc/ndiswrapper (for INF etc.) and hotplug - but what about my home folder?

Thanks and greetings,
Timo

---

