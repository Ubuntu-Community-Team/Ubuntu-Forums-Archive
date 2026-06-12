---
title: "Different video drivers?"
date: 2009-03-19
forum: Hardware
---

### Post by PM998 on 2009-03-19
Hi,

I run Ubuntu as a guest in a virtual box and from real hardware on a dual boot system.
The real hardware has an Nvidia graphics card and I installed the suggested drivers. Now the system does not boot in the VB anymore and gives a warning about a wrong configured graphics driver.
Is there a way to boot two different graphic drivers on ubuntu? Maybe some type of auto detection?

Thanks
   Peter

---

### Post by cariboo on 2009-03-19
A vm runs on virtual hardware, I would suggest starting in recovery mode and remove the nvidia drivers. If you are running VirtualBox install the guest additions, this should take care of your video problems.

JIm

---

### Post by PM998 on 2009-03-20
I have the guest addition installed and the drivers work fine, but the switch between the two drivers (NVIDIA for hardware and generic drivers for VB) is not automatically done and always requires a second boot. Is there a way to detect the system to load the appropriate drivers automatically?

Is there an alternative to the NVIDIA drivers? The main reason for their usage is the slow and stucking video rending without them?

Tks
  Peter

---

