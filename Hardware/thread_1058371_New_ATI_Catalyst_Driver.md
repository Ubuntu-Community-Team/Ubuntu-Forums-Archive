---
title: "New ATI Catalyst Driver????"
date: 2009-02-02
forum: Hardware
---

### Post by Venom_Man on 2009-02-02
I have a ATI Technologies Inc RV280 [Radeon 9200 PRO] and am wondering if using the new ATI driver will help me. Also how do i go about installing/using it.

---

### Post by jpeddicord on 2009-02-04
Moved to Hardware.

---

### Post by sowelie on 2009-02-04
Either use the proprietary driver from the repos (use System -> Administration -> Hardware Drivers).  Or, download and install from the ati website.  Honestly, the newer driver from the ati website is what I recommend, from my experience it works much better.

---

### Post by luvr on 2009-02-05
If you want to download the newer version of the driver from the ATI website, then there's also an installation manual that explains nicely how to install it.

You can create an Ubuntu-specific package first, and subsequently install that, so that it gets properly registered in your system's package database (i.e., you will find it back in Synaptic).

In my experience, it doesn't really work better than the version from the repos--but your results may be different, depending, e.g., on your exact hardware.

I've uninstalled the proprietary driver, and I'm running with the open-source one now. Thus, I cannot exploit the advanced features of the hardware (e.g., no compiz desktop effects, etc.)--but at least it doesn't give me any headaches, so it will have to do for now.

---

