---
title: "Will It Work With Intrepid"
date: 2009-01-03
forum: Hardware
---

### Post by measekite on 2009-01-03
If you are using an Unbuntu Feisty 7.04 Version on certain hardware that includes nvidia card, sound card, scanner, printer, monitor, dvd writer, cd writer etc and you have all of the drivers to make it work ok then here is the question:

If you reformat your hard disk and install Intrepid can you either:

Use the same drivers with Intrepid that you used with Feisty?

OR

Will there be updated drivers that you need to work with Intrepid?


Next Question:

Will you be able to use Intrepid without having to replace any hardware?

---

### Post by openn0de on 2009-01-03
1. Drivers are probably updated with releases. Im not sure about reusing drivers.

2. Intrepid probably hasn't had any major requirement changes, so it shouldn't need any new hardware.

---

### Post by lswb on 2009-01-03
drivers must match the kernel being used. When a new kernel version is installed it always bring in a new modules directory tree with drivers to match. In some cases, these drivers may have been compiled from the same source code as used in earlier versions. 

In general, hardware compatibility improves with newer releases, but there are certainly cases of things that stop working with a newer release. Why not try the live CD? If everything works OK from the CD it should work OK when installed too.

---

### Post by measekite on 2009-01-04
> **lswb said:**
> drivers must match the kernel being used. When a new kernel version is installed it always bring in a new modules directory tree with drivers to match. In some cases, these drivers may have been compiled from the same source code as used in earlier versions. 

In general, hardware compatibility improves with newer releases, but there are certainly cases of things that stop working with a newer release. Why not try the live CD? If everything works OK from the CD it should work OK when installed too.

I did try Live CD.  My system did work but with one exception that I am concerned about.  I have an NVIDIA GeForce 6600.  Under Feisty I was able to obtain a driver that allowed my system to use native mode of 1680x1050.  The driver version is:
[COLOR=DarkOliveGreen]
NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006[/COLOR] 

and the kernel version is:

[COLOR=Green]2.6.20-17-generic (#2 SMP Wed Aug 20 16:47:34 UTC 2008)

[COLOR=Black]I do not remember how I got the driver nor if I had to compile it.

As far as Live CD there was an option for me to write click and choose to se some 3D gnome screens.  When attempting to implement Intrepid put up a dialog box asking me to choose between Nvidia driver 173 or 175 (recommended).  First I tried 175 3 times and then I tried 173 a bunch.  Intrepid claimed the driver was tested. The driver downloaded but then when the install begain to take place the system put up a dialog box that a files install was attempted 6 times and failed and said it will attempt again in 90 seconds but the machine locked up.

This concerns me because without this driver the machine is worthless.  Feisty is no longer supported and I do not want to go back to Windows.
[B]
Any comments would be appreciated.  [/B]
[B]
How do I contact the powers to be at Ubuntu who produced Live CD and inform them?
[COLOR=Sienna]
Thank you in advance.  [/COLOR]
[/B][/COLOR][/COLOR]

---

