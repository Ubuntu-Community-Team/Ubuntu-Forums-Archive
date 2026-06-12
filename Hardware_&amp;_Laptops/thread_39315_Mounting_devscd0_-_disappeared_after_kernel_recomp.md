---
title: "Mounting /dev/scd0 - disappeared after kernel recompile"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by kheno on 2005-06-04
I recompiled the kernel, my new version is 2.6.11.10, i installed my ipw2200 card, and its worked fine(i recompiled it 'cause the ipw2200 wasnt working)...

My laptop is a intel sonoma so i have to use scsi to access the hd and cdrom(because i think both are sata baseaded), well, after recompiling, my /dev/scd0 disappeared :

it's my cdrom device, and i need so much to access some cd's ... and everything worked fine... only this happened... what can i do ?

thanks

kheno

PS: i have a dell d610

---

### Post by Pausanias on 2005-06-19
[QUOTE=kheno]I recompiled the kernel, my new version is 2.6.11.10, i installed my ipw2200 card, and its worked fine(i recompiled it 'cause the ipw2200 wasnt working)...

My laptop is a intel sonoma so i have to use scsi to access the hd and cdrom(because i think both are sata baseaded), well, after recompiling, my /dev/scd0 disappeared :

it's my cdrom device, and i need so much to access some cd's ... and everything worked fine... only this happened... what can i do ?

thanks

kheno

PS: i have a dell d610[/QUOTE]
 I'm having the same problem with a Dell Precision M70. When I boot into 2.6.10, the cdrom is there; when I boot in the 2.6.11, there is no /dev/scd0. I'm having a heck of a time trying to Google an answer to this. Have you gotten it working?

---

### Post by Pausanias on 2005-06-20
Check out this thread for a couple of solutions:

[http://ubuntuforums.org/showthread.php?t=42726](http://ubuntuforums.org/showthread.php?t=42726)

---

### Post by kheno on 2005-06-26
Hi Pausanias,

I tried some things posted at that link, but none worked for me...

Wich solutions worked for you ?

THanks

---

### Post by Pausanias on 2005-06-26
[QUOTE=kheno]Hi Pausanias,

I tried some things posted at that link, but none worked for me...

Wich solutions worked for you ?

THanks[/QUOTE]
 Upgrading to 2.6.12 did it for me. I've done a detailed write up of the how to on

[https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70](https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70)

---

### Post by bugmenot on 2005-08-20
If the above suggestions do not work, you probably have to enable SATA cdrom support in the kernel (which is not normally enabled by default). The following site has more info: [http://home.comcast.net/~canez/d610/](http://home.comcast.net/~canez/d610/)

But do try update the kernel first!

---

### Post by 23meg on 2005-09-14
exact same problem here with a Toshiba Tecra M4 sonoma laptop. i'll try the above solutions and report back.

---

