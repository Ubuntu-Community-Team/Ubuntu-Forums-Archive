---
title: "Radeon IGP320M fglrx doesnt support it?"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by timmytim on 2004-11-04
OK, I TRIED TO READ EVERY THREAD POSSIBLE ABOUT SIMILIAR PROBLEMS WITH THE ATI DRIVERS BEFORE I ASKEWD THIS, BUT I THINK MINE IS A BIT DIFFERENT. I HAVE AN HP 4560US LAPTOP WITH A RADEON IGP 320M VIDEO CARD, WHICH USES THE RADEON 7000 CHIPSET. FGLRX DOESNT SUPPORT THIS CARD, IT DOESNT SUPPORT NOTHING LESS THAN THE 8500. I WENT TO ATI'S WEBSITE TO TRY AND GET THE RADEON 7000 LINUX DRIVER - NO LUCK ONLY 8500 ON UP. WHAT CAN I DO? I TRIED THE FGLRX-DRIVER SEVERAL TIMES, AND AFTER I WRITE MY NEW XF86CONFIG-4 FILE, IT SAYS "PROBING PCI BUS FOR A SUPPORTED GRAPHICS DEVICE...UNABLE TO FIND ANY OF THE SUBSEQUENT BOARDS:" THEN IT LISTS THE SUPPORTED RADEON BOARDS, MINES ISNT THERE IF COURSE... ANY THOUGHTS?


tHANKS

---

### Post by Slovak on 2004-11-05
There currently isn't any regular linux support for you graphics, unless you use SUSE 9.1 pro and SUSE's own modified version of the ATI drivers for their modified kernel, then it will work according to various google search results.

---

### Post by wallijonn on 2004-11-05
Your only option may be to upgrade to XFree86 4.4: [http://www.xfree86.org/4.4.0/radeon.4.html](http://www.xfree86.org/4.4.0/radeon.4.html)

As Ubuntu uses libglibc 2.0, you may have to download a libglibc v2 version: [http://ftp.xfree86.org/pub/XFree86/4.4.0/binaries/Linux-ix86-glibc20/](http://ftp.xfree86.org/pub/XFree86/4.4.0/binaries/Linux-ix86-glibc20/)

[http://www.xfree86.org/4.4.0/Install3.html#3](http://www.xfree86.org/4.4.0/Install3.html#3)

---

### Post by daniels on 2004-11-06
[QUOTE=wallijonn]Your only option may be to upgrade to XFree86 4.4: [http://www.xfree86.org/4.4.0/radeon.4.html](http://www.xfree86.org/4.4.0/radeon.4.html)[/QUOTE]
No, no, no, no, no.  Don't do that.  At all.

We have backported the patch for IGP support to our 4.3 packages, and using 4.4 will only cause you quite immense pain.

---

### Post by daniels on 2004-11-06
You don't need any wacky drivers, by the way -- the one installed with standard Ubuntu will work just fine.

---

### Post by timmytim on 2004-11-06
It does work fine for 2d, but how can i get 3d accelration? Also, i saw that the 2.6.9 kernel had some kind of support for the IGP chipsets. I was gonna go that route because I am going to recompile my kernel anyway.

---

### Post by wallijonn on 2004-11-07
[QUOTE=daniels]No, no, no, no, no.  Don't do that.  At all.

We have backported the patch for IGP support to our 4.3 packages, and using 4.4 will only cause you quite immense pain.[/QUOTE]

Good thing to know. I'm glad that I am satisfied with Ubuntu working with my 9800 Pro.

---

### Post by daniels on 2004-11-07
[QUOTE=wallijonn]Good thing to know. I'm glad that I am satisfied with Ubuntu working with my 9800 Pro.[/QUOTE]Which is not an IGP card.

---

### Post by timmytim on 2004-11-08
Thanks for all the tips!. I think, after some long thinking, i'm taking Ubuntu off the Laptop. Its just not worth it to me, plus i dont have the time, to fix all the problems with the hardware issues :(  I have just installed Ubuntu on my home pc and it works beautifully! I love this distro. No hardware problems at all!!! I have a geforce fx5500, installed the driver throught synaptic, no problems at all. 1300+ fps in glxgears! Thanks again.

-Hooked on Ubuntu-
                 =P~

---

### Post by noriise on 2007-01-17
whats the outcome for this? i have same laptop and graphics, and was even considering installing beryl?

At least i think i need a new gfx driver so i can use both laptop screen and another monitor?

any ideas... much appreciated, relative newbie enjoying the linux

cheers

---

