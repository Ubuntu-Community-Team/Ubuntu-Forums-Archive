---
title: "Compaq presario R4000"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by Nevermore on 2005-12-25
Hi all
i tried to install Ubuntu 64bit on my compaq presario, but results were quite odd, i had to turn OFF framebuffer on the installation otherwise i couldnt even get to language selection, then after installing, gdm was not working (i just got alot of colorful lines). I tried to start from live64 but no luck, even live for i386 didnt do any good. then i ended up with a locked system, since even entering it in safe mode didn-t allow me to do dpkg-reconfigure xserver.xorg.
is there something i can try for the installation of ubuntu on this lap?
Thanks

---

### Post by Nevermore on 2005-12-26
[QUOTE=Nevermore]Hi all
i tried to install Ubuntu 64bit on my compaq presario, but results were quite odd, i had to turn OFF framebuffer on the installation otherwise i couldnt even get to language selection, then after installing, gdm was not working (i just got alot of colorful lines). I tried to start from live64 but no luck, even live for i386 didnt do any good. then i ended up with a locked system, since even entering it in safe mode didn-t allow me to do dpkg-reconfigure xserver.xorg.
is there something i can try for the installation of ubuntu on this lap?
Thanks[/QUOTE]

i tried my best to override the problem, but seems that video drivers for ATI are not working at all.
the only thing i get are colorful lines, and i am not able to see a bash in order to reconfigure xorg with vesa...

---

### Post by Nevermore on 2005-12-29
i found out that the only one that works is Dyne:bolic, pretty fast and neat..
but i am used to ubuntu and i WANT ubuntu..
any help?

---

### Post by Nevermore on 2005-12-30
ok i was able to start ubuntu:
used the code VGA=792 at booting
then logged in in recovery mode and gave dkpg-reconfigure xserver-xorg
choose vesa and everything went fine..
seems ati drivers are damn buggy

---

