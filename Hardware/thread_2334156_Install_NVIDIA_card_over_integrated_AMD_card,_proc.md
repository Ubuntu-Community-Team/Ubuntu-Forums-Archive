---
title: "Install NVIDIA card over integrated AMD card, processor and motherboard?"
date: 2016-08-16
forum: Hardware
---

### Post by canhoto on 2016-08-16
Hi.

With the upgrade to 16.04, as you probably know, there's no proprietary driver for AMD graphics cards. We have to stick to the opensource driver included in the kernel, which is great, but doesn't work with certain software (like Steam or X-Plane). This is the fault of ATI/AMD, of course (lack of support for Linux).
Anyway, here I am with an all AMD environment: motherboard with integrated graphics and processor. All AMD/ATI.

So, what I would like to know is if I can buy a NVIDIA (or Intel) PCIe card and use it over my current motherboard, AMD processor and AMD graphics card.
- Will that work out of the box - just plug and play?
- If not, how easy is it to make it work (if it's possible)?
- Are there any recommended PCIe NVIDIA cards for Steam and other games which are no too expensive?

Thanks!

---

### Post by deadflowr on 2016-08-17
Plug and Play? most likely yes.
Double check the graphics card settings in the BIOS/UEFI to make sure the card's pci/pcie slot isn't in a disabled state.
(Or something to that affect.)
That can happen sometimes where the setup has the VGA/GPU set to the integrated card and the pci/pcie setting is off.
More likely a setup on older machine, newer machines usually have that set to an auto-phase where as the system will use the pci/pcie card if there, and use the integrated card if no pci/pcie card, by default.

Most anything else you would have to do is similar to what you would have done with getting the AMD drivers up and running.
That being open the additional drivers tab in software and updates and look at the drivers it lists and install one you think might work best based on the card you get.

No comment on recommended cards.
Leave that to steam users.

---

### Post by QIII on 2016-08-17
> **canhoto said:**
> This is the fault of ATI/AMD, of course (lack of support for Linux).

Incorrect.  What is going on right now is precisely because of AMD's ***support*** for Linux.  They are going through a huge transition and re-structuring of the entire scope of their drivers to give the open source community exactly what we have been asking for for years:  Full featured open-source drivers.  AMD is, after all, a member of the Linux Foundation.

Radeon has improved by leaps and bounds.

AMDGPU has been introduced to support the new technological capabilities of AMD's cards.

AMDGPU Pro, the proprietary driver, is based on AMDGPU.

I run AMDGPU with an R9 380X and its performance is *better* than fglrx.

This is a transition period.  Frustrating?  Yes.  Indicating a lack of support from AMD?  Absolutely not.

Please do not give in to FUD.

Nevertheless, you may indeed want to use an Nvidia card right now.  Use what works.  Remember to remove the fglrx driver if you have attempted to install it.  In your BIOS/EFI, make sure that you set PCI-e as your preference for your graphics adapter.  That will make sure that the PCI-e card is used rather than the integrated GPU.

---

### Post by mastablasta on 2016-08-17
or just install 14.04 and wait for the drivers to be developed well, and then move to 16.04.

---

