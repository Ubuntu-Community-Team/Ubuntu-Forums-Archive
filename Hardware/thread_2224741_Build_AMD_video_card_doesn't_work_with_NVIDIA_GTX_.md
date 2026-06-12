---
title: "Build AMD video card doesn't work with NVIDIA GTX 650 stick with 12.04 to avoid this"
date: 2014-05-17
forum: Hardware
---

### Post by mcfardo907 on 2014-05-17
I am having a problem since I upgraded from Ubuntu 12.04 to 13.10. I have an AMD A10 Cpu with an integrated Radeon HD 7660D video card. I also have a NVIDIA gtx 650. They worked and played well when I had Ubuntu 12.04 installed. I like the extra processing power that the APU gives, and it helps shoulder the load. I have to disable the Radeon integrated graphics card if I want to be able to get my system to boot into Ubuntu 13.10. They work and play and well with each other when I am using my windows 7 partition. What happened between ubuntu 12.04 and ubuntu 13.10, and is there a way to fix it? Here's the full specs for my PC. 

CPU: AMD A10-5800K APU
Memory: 8 gigs of RAM
OS: Ubuntu 13.10
Motherboard: ASUS F2A55-M LK PLUS
APU video card: Radeon HD 7660D
External video card: NVIDIA GTX 650

Any help or at least someone telling me I am out of luck would be appreciated.

---

### Post by robbo.stanley on 2014-05-18
I don't know, but it could be to do with the drivers for your Radeon graphics card, have you updated them?

---

### Post by QIII on 2014-05-18
Hello!

You are likely to run in to problems if you have both enabled.  ATi/nVIDIA mixes do not work well with Linux.  My question would be how you got both to work together before, because that would be very useful to know!

I would probably disable to ATI GPU on the die using the BIOS/EFI and set the PCI card to be the primary output.  Then install the nVIDIA driver.

The APU would stay cooler and the dedicated GPU would probably give you better graphics performance, anyway.

Otherwise, I'd remove the nVIDIA card and use it elsewhere.

Cheers!

---

### Post by mcfardo907 on 2014-05-19
> **QIII said:**
> Hello!

You are likely to run in to problems if you have both enabled.  ATi/nVIDIA mixes do not work well with Linux.  My question would be how you got both to work together before, because that would be very useful to know!

I would probably disable to ATI GPU on the die using the BIOS/EFI and set the PCI card to be the primary output.  Then install the nVIDIA driver.

The APU would stay cooler and the dedicated GPU would probably give you better graphics performance, anyway.

Otherwise, I'd remove the nVIDIA card and use it elsewhere.

Cheers!

Thank you for the advice and I appreciate the response. I'll probably upgrade the memory from 8 gigs to 16 gigs at some point, and that should help out as well. The APU in the AMD chip is in essence a built in video card that's separate from the CPU, but integrated on the same chip. The NVIDIA card is set as the primary. I have PCI selected instead of integrated IGFX  I backed up my data and went back to ubuntu 12.04. That version does work and play with both cards enabled. 12.04 is a LTS and hopefully will serve many years. Everything after that seems to have problems They work and play well on my Windows drive as well, and I do notice an improvement in performance in my video games when I have the APU enabled. I'll probably upgrade the memory from 8 gigs to 16 gigs at some point. I'll mark this solved or at least workaround.

---

