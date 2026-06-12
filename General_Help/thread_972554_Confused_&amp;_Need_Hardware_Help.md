---
title: "Confused &amp; Need Hardware Help"
date: 2008-11-05
forum: General Help
---

### Post by UltimateGorgon on 2008-11-05
I am coming from the Microsoft camp, so please take it easy.

Currently, I am running a desktop computer using Windows Vista Home Premium 64-bit.  My processor is an AMD Athlon 64 X2 2.8GHz.

I downloaded the free Virtual Box program and I am attempting to install Ubuntu 8.10 Server 64-bit.  Every time I try to install though it says:

"This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU."

If Ubuntu says my CPU can't handle a 64-bit kernel, how did I install Vista 64-bit?

---

### Post by sillyxone on 2008-11-05
I never use free Virtual Box before so I'm not sure, but seems like Virtual Box can only emulate 32-bit CPU and thus does not support 64-bit guest OS. 

Check their documentation and website to see if 64-bit guest will be supported soon.

---

### Post by m_l17 on 2008-11-06
I have being reading the VirtualBox manual and it states:

> 1.6 64-bit guests
Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems,
under the following conditions:
   1. You need a 64-bit processor with hardware virtualization support (see chapter
      
      1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 10) and a 64-
      bit host operating system.
   
   2. You must run a 64-bit version of VirtualBox on that OS (Windows Vista, Linux or
      OpenSolaris). This can then run both 32-bit and 64-bit VMs; a 32-bit VirtualBox
      can only run 32-bit VMs, regardless of the hardware.
   
   3. You must enable hardware virtualization; software virtualization is not sup-
      ported for 64-bit VMs.


You need to enable hardware virtualization in your bios, but I suggest you read the muanal.

You can get the manual here:

[http://www.virtualbox.org/wiki/End-user_documentation]("http://www.virtualbox.org/wiki/End-user_documentation")

I also suggest asking in their forums with any problems:

[http://forums.virtualbox.org/]("http://forums.virtualbox.org/")

---

