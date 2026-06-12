---
title: "NVIDIA graphics card not enabling effects"
date: 2010-01-21
forum: Hardware
---

### Post by Frederico86 on 2010-01-21
Hi, I'm completely new to the Linux Ubuntu world. However I have managed to get my driver installed, and activated it through System>Admin>Drivers.
However I cannot seem to enable the effects in the Appearance window. Whenever I select either Normal or Extra, the screen flashes and it says "Desktop effects cannot be enabled". I am completely baffled by this as I assumed I just had to install the NVIDIA drivers for this. I can access the NVIDIA display settings panel and change my resolution, Max - 1440 X 900.
I am using a NVIDIA Gforce Go 7600

Thanks

I have just run a script to check if compiz will work on my laptop. This is it's output:
Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

I don't think my graphics card is incapable of all this so could really do with some advice......

---

### Post by ephman on 2010-01-22
what version of xorg are you running?  i'm having a similar problem after an update.

---

