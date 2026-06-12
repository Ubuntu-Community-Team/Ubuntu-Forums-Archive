---
title: "Tecra a10 ubuntu 8.04.1 install problem"
date: 2008-10-15
forum: Hardware
---

### Post by obaino on 2008-10-15
I tried installed Ubuntu 8.04.1 using the alternate cd. The installation seemed ok, so I reboot. I can see the ubuntu logo, but once I get to the log in screen everything is scrambled. I cannot use it. I had to do CTRL-ALT-F1 to get a terminal and reboot...

Any ideas on what to do? I guess it's my graphics card, but I don't know what to do from the terminal screen to fix this.

Mobile Intel® GMA 4500MHD, up to 1,340 MB total available graphics memory with 3 GB system memory, 16x PCI Express.
Screen Resolution             1280 x 800 Pixels

Any contribution is really appreciated.

---

### Post by nlp on 2008-12-05
Same problem here.  The easiest solution is probably just to install Ubuntu 8.10 (Intrepid).  The Intel graphics and networking (including wireless) seem to work just fine with this new edition.  Sound is still non-existent, though.

I did some googling and there are a couple of reports of sound problems with the Tecra A10, but no proposed solutions.  Other than sound though, the system seems usable with Intrepid.

---

### Post by KenLazlo on 2009-02-11
I got sound working on my Tecra A10 running Ubuntu 8.10 x64 by adding 

options snd-hda-intel model=toshiba

to /etc/modprobe.d/alsa-base

Greetings from Germany

---

