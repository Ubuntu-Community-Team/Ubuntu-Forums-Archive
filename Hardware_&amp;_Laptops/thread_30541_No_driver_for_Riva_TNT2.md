---
title: "No driver for Riva TNT2"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by Zensunni on 2005-04-29
I'm stuck in the command line because the GUI doesn't have a driver for the TNT2. I've tried using nvidia's linux driver, but that doesn't work either. Here is what it tells me:

"No precompiled kernal interface was found to match your kernal; would you like the installer to attempt to download a kernal interface for your kernal from the NVIDIA ftp site? (yes/no)

No matching precompiled kernal interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel.

....so how do I go about doing that? Or is there a better way?

---

### Post by odix on 2005-04-29
do you try to install nvidia drivers directly or via apt (or synaptic or aptitude) ?

---

### Post by Zensunni on 2005-04-29
I just burned the driver onto a CD on my windows computer, then typed "sh <driverfilename>.run" when I was in linux.

How do I install via apt or the other two?

---

### Post by odix on 2005-04-29
There is a section in the ubuntu starter guide you may found information [here](http://www.ubuntuguide.org/#installnvidiadriver) . There is also a link to add repositories. The simpliest way is to us synaptic, if you have a gui, if not use the given link.

odiX

---

### Post by Zensunni on 2005-04-29
Ah, yes - it's all up and running. Thanks a truckload!

---

