---
title: "video card problem after upgrading to 8.10 (pic inside)"
date: 2008-12-23
forum: Hardware
---

### Post by shaolinchamp on 2008-12-23
so i recently upgraded from 8.04 to 8.10. when i rebooted in the new 8.10 installation, it gave me this message  (ubuntu in low graphics mode Your screen, graphics card and input device settings could not be detected correctly, you will need to configure them yourself.)  so i just chose to boot it in low graphics mode so it lods up the login screen and i login.  as it is booting to desktop i see this (pic below)



ive tried to fix it myself but have gotten nowhere, any info would be highly appreciated.  i have a ati radeon x550.  it was working fine before i upgraded

---

### Post by fudo on 2008-12-23
@Shoalinchamp - I just upgraded my graphics card to an ATI Radeon based card, with Ibex(x64) and was experiencing some funny issues initially, but then I found this guide.

[URL="http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide"]http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide
[/URL]

Have a look at that and post back if you get stuck!


fudo

---

### Post by shaolinchamp on 2008-12-24
> **fudo said:**
> @Shoalinchamp - I just upgraded my graphics card to an ATI Radeon based card, with Ibex(x64) and was experiencing some funny issues initially, but then I found this guide.

[URL="http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide"]http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide
[/URL]

Have a look at that and post back if you get stuck!


fudo
  most of the solutions on this guide is when your actually on the desktop, i cant see anything on the screen once it boots up

---

### Post by shaolinchamp on 2008-12-24
is there any way i can downgrade from the shell

---

### Post by prak97 on 2008-12-24
try booting Ubuntu in "recovery mode" it should give you a low res screen . from there you can probably adjust your settings.
But I suspect your Graphics card driver needs installing .
I've been through this painful process recently.

---

### Post by shaolinchamp on 2008-12-24
you mean recovery mode with the kernel or from the login screen?? i tryed with the login screen and it gave me the same screen

---

### Post by prak97 on 2008-12-24
mmmm.... I have a dual boot with Vista ...and I use Grub ...so I get the option to boot in recovery mode in Grub...That drops me to a low res login .
But as for the problem you have ....I had something similar and I used "envyNG" to install the video card driver ....since then it's been OK.
 ( just Google it ) 
Cheers

---

### Post by prak97 on 2008-12-24
Oh !  I have an Nvidea card ....( envy NG is for Nvidea cards ). You don't say what your system has .

---

### Post by shaolinchamp on 2008-12-24
yeah, i have an ati radeon card.  im booting in recovery mode and trying the solution that fudo provided

---

### Post by shaolinchamp on 2008-12-24
thank you fudo, your information helped me alot, and im now using my firefox in ubuntu:)

---

