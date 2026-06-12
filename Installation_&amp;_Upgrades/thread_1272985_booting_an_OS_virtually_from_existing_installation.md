---
title: "booting an OS virtually from existing installation"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by geoffm on 2009-09-22
say, if I actually have a working WinXP installation on my computer, but I'd like to boot it virtually while still running ubuntu. without having to reboot. what should I use? it seems like VirtualBox doesn't give me that option.

---

### Post by lemming465 on 2009-10-03
I'm not sure about booting physical parititions in virtualbox; I have done it with vmware in the past.  However, you can't usually expect to be able to boot something both native (on the bare hardware) and virtually, as the virtual device emulation usually has different devices, and the drivers are all different.  So expect some OS repair work if you get the virtual boot going.

---

### Post by Mark Phelps on 2009-10-03
Virtual solutions require fresh installations of their resident OSs.  If you want to use XP in Virtual Box (or any other Virtual solution), you will need to reinstall it from scratch.

I've read about folks figuring out how to reuse an existing OS installation, but it always resulted in some form of filesystem corruption, and in the case of Vista, it forced deactivation of the OS on every boot.

---

