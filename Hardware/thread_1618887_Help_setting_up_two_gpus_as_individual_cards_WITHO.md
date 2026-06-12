---
title: "Help setting up two gpus as individual cards WITHOUT sli/crossfirex bridge(s)"
date: 2010-11-11
forum: Hardware
---

### Post by npm1 on 2010-11-11
Help setting up two gpus as individual cards WITHOUT sli/crossfirex bridge(s)

hi i've a new computer build with the following spec....:
870A Fuzion with Lucid Hydra chipset
Amd Phenom II x6
4gb ddr3 memory
500gb 7500rpm hardrive
ubuntu 10.04
palit 1gb gts 450
palit 2 gbgtx 460
CASECOM KM 9788 case

i've already fitted the two graphic cards----I DON'T WANT SLI(or connected together)---
how do i make them both available for use with octaneGPU rendering software alongside blender....

---

### Post by Fafler on 2010-11-11
Have you tested if it actually works? It should do so out of the box.

Install drivers and X will autoconfig the first card with your monitor connected, and CUDA applications should be able to see both cards.

---

