---
title: "compiling a newer version of grub unto 9.10?"
date: 2010-02-12
forum: Hardware
---

### Post by akos.maroy on 2010-02-12
I wonder how one can compile a newer version of grub into 9.10?

I'm installing Ubuntu 9.10 on a brand new HP Envy 15, and it seems the raid controller in the laptop is just too new for grub 1.97-beta4 that comes with 9.10.

if I install 10.04-alpha2, it recognizes my raid controller properly. but unfortunately 10.04-alpha2 is really alpha, and for example suffers from a lot if screen corruption issues.

so I decided to compile & install a newer kernel into 9.10 - which seems to work fine. but still, the grub that comes with 9.10 just cannot work with the raid controller in the machine. I rebuilt the same package in the hope that with the 2.6.32.8 kernel headers it would work - but it doesn't.

so: how does one build packages of a more recent grub on an ubuntu system? or should I just try to install the deb from 10.04 alpha2?

---

### Post by IcarusR on 2010-02-12
Download grub .deb from 

[http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/grub2/]("http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/grub2/")

---

