---
title: "thinkpad w520 Nvidia Optimus &amp; 16.04"
date: 2016-11-26
forum: Hardware
---

### Post by timrichardson2 on 2016-11-26
About a week ago I bought a bargain Thinkpad w520. It comes with an Nvidia Quadro 1000 & Intel card, with swapping handled by Optimus.
I found some tips on forums, and the laptop works very well in dual screen mode if I force it to 'discrete' graphics in the BIOS. 
I'm using the Nvidia 367 driver. I should say that this is my first experience of using Ubuntu 'on the metal' for a few years, in fact it is partly an experiment to see how it goes for me. So far it has been an incredibly impressive result. I can't believe how well this quadcore five year old machine runs (AUD $400, with 6 hour battery life with the Intel driver in use, so even the battery is good). 


I have one irritation, which is puzzling me. If I use the machine in "Optimus" mode, and have it in Nvidia mode, the laptop panel is not seen by my Xwindows session, only the external monitor. That is, the laptop panel is not detectable by X. I can use it for virtual consoles (alt-F1).

How should I track this down? It works if I start in Discrete Driver (i.e. I force the Nvidia driver via bios) so something is different about initialisation of drivers.

My grub cmd line has some tweaks to get it to boot (without these, it doesn't boot if I am using the Nvidia driver). 


```
GRUB_CMDLINE_LINUX_DEFAULT="agp=off quiet splash acpi_osi=linux thinkpad-acpi.br
ightness_enable=1 nox2apic zswap.enabled=1"
```

---

### Post by timrichardson2 on 2016-11-26
In dedicated Nvidia mode (via BIOS):
```
  lspci | egrep "3D|VGA"
```
shows only the nvidia driver.

But when I start in optimus mode, I see both drivers present. 

```
tim@w520:~$ lspci | egrep "3D|VGA"
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [Quadro 1000M] (rev a1)
tim@w520:~$ 

```

---

