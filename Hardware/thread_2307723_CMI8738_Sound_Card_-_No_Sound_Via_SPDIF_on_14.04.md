---
title: "CMI8738 Sound Card - No Sound Via S/PDIF on 14.04"
date: 2015-12-27
forum: Hardware
---

### Post by CelticWhisper on 2015-12-27
I have installed a CMI8738 sound card ([this exact model]("http://smile.amazon.com/SIIG-SoundWave-7-1-PCI-IC-710012/dp/B0006HDF6S/ref=cm_cr_pr_product_top?ie=UTF8")) and am unable to hear any sound over the S/PDIF output.  Alsamixer shows that it's disabled.  I was able to get sound via my motherboard's onboard TOSLINK port (using an optical->coaxial converter for my speakers), and the sound control panel recognizes the device as a CMI8738/C3DX PCI Audio Device, so it seems that the card is recognized.

I have found instructions for configuring ALSA in Arch Linux for this card, but my understanding is that Ubuntu uses PulseAudio instead and some ALSA config files were not in /etc where the other forum posts and articles said they would be.

Please help.  Thank you very much.

---

