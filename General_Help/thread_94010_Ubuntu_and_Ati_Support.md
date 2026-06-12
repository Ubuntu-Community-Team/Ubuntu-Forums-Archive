---
title: "Ubuntu and Ati Support"
date: 2005-11-23
forum: General Help
---

### Post by Tha1 on 2005-11-23
My Ubuntu Breezy keeps freezing, randomly, all the time. Has anything to do with the fact that I have an ATI 7000 64 MB(Gecube) as the video card?And if it does,how can I be sure that it is supported in Breezy?
I looked in the HardwareSupportComponentsVideoCards and there is an ati 7000 listed,but I have doubts... :oops:

---

### Post by 23meg on 2005-11-23
Take a look at your system logs (Applications / System Tools / System Log) after crashes to see if any video related errors are reported. Also see if ```
dmesg |grep ati
``` brings up anything unusual.

---

### Post by Tha1 on 2005-11-24
I saw the logs and there's nothing related to video.
when I execute that command,this is the output:


-----------------------------------
[4294673.631000] NFORCE2: not 100% native mode: will probe irqs later
[4294678.478000] ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
[4294678.558000] ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
[4294678.658000] ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller

Should not say anything related to ATI or to the video card?

---

### Post by Pablo_Escobar on 2005-11-24
Tha1 did You install the drivers for Your graphic card ??

---

### Post by Tha1 on 2005-11-24
The thing is,in the ATI site they only have drivers for 8500 or later.

---

