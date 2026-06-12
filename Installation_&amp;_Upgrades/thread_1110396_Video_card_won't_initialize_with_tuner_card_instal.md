---
title: "Video card won't initialize with tuner card installed"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by wheniwork on 2009-03-29
Hi. I was able to install 8.10 and get the nvidia drivers installed and working correctly. However, once I installed my two PCI hd-5500 tuner cards the NVIDIA graphics device fails to initialize. I get this error:

Failed to initialize the NVIDIA graphics device PCI:1:0:0

If I take out one of the tuner cards the graphics driver loads up fine and all is good. I have found nothing to help with this type of issue. I am hoping someone can shed some light on.

MotherBoard is Gigabyte GA-EP45-UD3P
Graphics Card is MSI NX8400GS (nvidia)
Tuner Card is PCHDTV hd-5500 (two are installed)

I am taking out the tuner card in PCI slot 2. The other tuner card is in PCI slot 1 and things load up fine with the single tuner card installed.

thanks!

---

### Post by cariboo on 2009-03-29
Run

```
lspci
```

to see if the device id has changed. Look for a line that looks similar to this:

```
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
```

Jim

---

### Post by wheniwork on 2009-03-29
Well. It reads the same with or without the second tuner card.

With the second tuner card it reads...
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

```

WithOUT the second tuner card it reads the same
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
```

Any ideas....?

---

### Post by wheniwork on 2009-03-30
I'm still having no luck. With one tuner card installed the video card drivers load fine... but with the second the video drivers do not load.... 

I thought perhaps it may be an IRQ issue, but I don't know how to test for that. 

Thanks in advance!

---

