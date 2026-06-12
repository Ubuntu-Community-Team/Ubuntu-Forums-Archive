---
title: "Using Feisty with 2x Nvidia 6800GT's in SLI"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by tehpopa on 2007-04-27
Here's the issue:

I have a 98%(damn you mythtv and SLI) perfect running Ubuntu install, which for me and Linux has set some sort of record. I can run on one video card just fine, but I'd really like to get SLI working. I have two 6800GT's, that work excellent under Windows. None of the hardware has changed between my Windows install and my Ubuntu install, but I can't get SLI to work with Ubuntu. Proper NVidia drivers are installed and working excellently with one card. When I set my xorg.conf file(attached) to have the option:

```
Option "SLI" "1"
```

It will load X, but yell at me in my log file(attached). This is the error I get:

```
(EE) NVIDIA(0): Failed to find a valid SLI configuration!
(EE) NVIDIA(0): Invalid SLI configuration 1 of 1:
(EE) NVIDIA(0): GPUs:
(EE) NVIDIA(0):     1) NVIDIA GPU at PCI:5:0:0
(EE) NVIDIA(0):     2) NVIDIA GPU at PCI:4:0:0
(EE) NVIDIA(0): Errors:
(EE) NVIDIA(0):     - Chipset not approved for SLI
(WW) NVIDIA(0): Failed to find a valid SLI configuration for the NVIDIA
(WW) NVIDIA(0):     graphics device PCI:5:0:0.  Only one GPU will be used for
(WW) NVIDIA(0):     this X screen.  Please see Appendix W: SLI and MultiGPU
(WW) NVIDIA(0):     FrameRendering in the README for troubleshooting
(WW) NVIDIA(0):     suggestions.
```

Does anyone have any ideas what I borked? Thanks :)

---

### Post by ratal on 2007-10-24
I would say correct syntax is : "SLI"** "on"**

---

