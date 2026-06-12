---
title: "newb + conexant modem = problems"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by VitaminG on 2005-09-02
As the title suggests, I am a total newb :???: , and I can't get my conexant modem installed. I downloaded the 1/4 speed drivers from linuxant(both the installer and the .deb package), but the Installer asks to connect to the internet ](*,) to download the .deb package. how can I get it to read from the HD instead of going to the net?
In case it makes a difference, I'm running a home-built that I made from old computer parts. I have a dual-boot setup with Windows 2k, which is the only reason I've even gotten this far(leave it to microsoft to force a person to feel grateful. :mad: )
Thanks in advance for any help.

EDIT: My modem's an HCF.

---

### Post by az on 2005-09-02
I do not know about their packages; they sell them, so you should ask them for specifics.

Any module can be compiled by downloading the source and compiling it.

unpack the source and read the readme as to how to compile it.

tar xvzf (file.tar.gz)  (or just use nautilus)


You need to install the build-essential and linux-headers-2.6.10-5-386 packages.  They are on your cd.  I doubt prebuild debian packages will work, since debian uses a differnet version kernel.

---

### Post by VitaminG on 2005-09-03
Thanks for the advice, but it turns out that, on closer inspection, I downloaded the wrong package. once I got the right files downloaded, i just used "dpkg -i" and the install went smoothly.

---

