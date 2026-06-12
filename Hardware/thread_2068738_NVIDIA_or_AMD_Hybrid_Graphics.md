---
title: "NVIDIA or AMD Hybrid Graphics?"
date: 2012-10-09
forum: Hardware
---

### Post by wmaciel on 2012-10-09
I'm about to buy myself a new notebook and I've been wondering about the whole Hybrid Graphics problem.
I've had a Dell XPS 15 with a NVIDIA Optimus Graphics Card for a while now, and I'm really not very happy with the way bumblebee and ironhide "solved" the problem.

I've looked into some AMD Radeon Graphics Cards and I haven't found many people complaining about problems with the switch between the discrete and integrated cards.

But apparently AMD made a lot of attempts on this energy saving field, and things got a little messy, there is Enduro tecnology, zero core technology and so on.

My questions basicaly are:
Do you think it is a good idea to stay away from optimus and NVIDIA and try AMD?
Which one is working better with ubuntu? 
I do a lot of OpenGL, OpenCL programming as well as gamming, do you recommend a specific notebook?

Thank you for any replies

---

### Post by typhoon_tip on 2012-10-10
Well, you can either go with any NVIDIA or AMD if you choose a T series Lenovo ThinkPad laptop, as they allow you to control the behavior of the graphics trough the BIOS, and they are generally very reliable.

---

### Post by wmaciel on 2012-10-10
> **typhoon_tip said:**
> Well, you can either go with any NVIDIA or AMD if you choose a T series Lenovo ThinkPad laptop, as they allow you to control the behavior of the graphics trough the BIOS, and they are generally very reliable.

Thank you I'll look into this BIOS control. Any early leads?

---

### Post by QIII on 2012-10-10
I would even steer clear of the ATI hybrids unless the ATI GPU IS A 6XXX OR 7XXX series. (Careful. Some notebooks say they have a 6xxx series card when what they have is really an over-clocked and over-volted 5xxx series GPU.)
 
ATI dual graphics (two ATI GPUs) work well, but AMD is changing all HD 4xxx and prior GPUs to legacy support, which means the driver will not work with x server after Ubuntu 12.4. So both GPUs would have to be HD 5xxx series or later.
 
If you go with hybrid ATI/Intel graphics, and you can switch via the BIOS/EFI, make sure the GPU is a 5xxx series or better. If no BIOS switch, make sure the GPU is a bona fide 6xxx or 7xxx series so you can switch through Catalyst.
 
Support/functionality of Intel/ATI and Intel/NVIDIA graphics in Linux is in flux right now.  Personally, I would not buy a machine with hybrid graphics at the moment.

---

