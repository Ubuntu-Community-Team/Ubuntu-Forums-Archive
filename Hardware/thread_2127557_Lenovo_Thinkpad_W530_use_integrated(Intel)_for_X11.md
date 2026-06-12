---
title: "Lenovo Thinkpad W530: use integrated(Intel) for X11 and discrete(NVIDIA) for CUDA dev"
date: 2013-03-20
forum: Hardware
---

### Post by grossetti on 2013-03-20
Hi,

I have a Lenovo Thinkpad W530 running Linux and it has two graphics cards, an Intel (integrated) and an NVIDIA (discrete). It has a BIOS option for  choosing which graphics card to use or use optimus  (integrated/discrete/optimus).

I was thinking of running X11 on the Intel card and CUDA programs on the  NVIDIA card, that way I can debug CUDA on X11 (effectively use the  NVIDIA card as a calculation GPU and not for actual output).

Also, I would like to be able to disable the NVIDIA card when I don't need it. I understand that if I use Optimus I need bumblebee to switch between cards, however I do not think this is what I need as I don't want to use X11 on the NVIDIA card (Optimus basically pipes the data from the Intel card to the NVIDIA card, thus it would be using the NVIDIA card for X11,unless I am mistaken). I think I need to select integrated in the BIOS and somehow get CUDA to use the discrete card.

I was wondering if anyone has tried this?

Thanks,
Gabriel

---

