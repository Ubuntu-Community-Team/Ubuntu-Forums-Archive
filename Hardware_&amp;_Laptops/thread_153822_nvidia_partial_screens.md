---
title: "nvidia partial screens"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by manuzza on 2006-04-01
I have a new laptop, the Toshiba Tecra M5, with 2GHz dual core, and an nvidia Quadro with 128 Mb VRAM.

The default Dapper install automatically gave me the beautiful 1400x1050 native resolution, but there was no GL acceleration. I have successfully added the nvidia GLX drivers (glxgears is now smooth) but they introduced a new problem: I only get a "viewport" of the chosen screen resolution.

For example, when I select 1400x1050, I only see (approximately) 1224x918, with the rest off the screen (maximising an application means the bottom and right sides are off the screen, but a screenshot shows they are actually there). It won't scroll to the unviewable areas.

But if I drop the resolution to something lower, I get the same problem. For example, if I use 1024x768, I can only see 894x673.

The relevant lines from xorg.conf are:

```
Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection
```


Any suggestions for fixing this?

Murray.

---

### Post by SethD on 2006-04-06
Sorry, I don't have a suggestion about your video card, but I was wondering if you had the audio working? I've heard of people having problems with the new SigmaTel STAC 9200. Has it been working fine for you?

Thanks, Seth

---

