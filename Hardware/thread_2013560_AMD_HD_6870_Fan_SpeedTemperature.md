---
title: "AMD HD 6870 Fan Speed/Temperature?"
date: 2012-07-01
forum: Hardware
---

### Post by Loser777 on 2012-07-01
I've noticed that my graphics card is much louder in Ubuntu 12.04 than in Windows and that it also runs noticeably hotter. Is this just a case of the Ubuntu drivers not being as well optimized?

---

### Post by QIII on 2012-07-01
Have you installed the proprietary AMD/ATI driver?   If you have not installed the proprietary AMD/ATI driver, you are using  the default open source driver (which is not really a specifically  "Ubuntu" driver), which is capable (and quite good of late).   However,  some users do note heat issues.

Unlike Windows, which has access to the Microsoft driverbase to make things "Plug 'n' Play" by automatically installing drivers, many hardware components require that you install the drivers deliberately in Linux distributions.  With Ubuntu, there is a repository containing the AMD/ATI driver.  However, it has to be installed by the user.

Have a look at the ATI Driver Wiki link in my signature if you don't have the proprietary driver installed and you want it.   If the wiki doesn't make any sense to you, I'll help walk you through it.

---

### Post by Loser777 on 2012-07-03
> **QIII said:**
> Have you installed the proprietary AMD/ATI driver?   If you have not installed the proprietary AMD/ATI driver, you are using  the default open source driver (which is not really a specifically  "Ubuntu" driver), which is capable (and quite good of late).   However,  some users do note heat issues.

Unlike Windows, which has access to the Microsoft driverbase to make things "Plug 'n' Play" by automatically installing drivers, many hardware components require that you install the drivers deliberately in Linux distributions.  With Ubuntu, there is a repository containing the AMD/ATI driver.  However, it has to be installed by the user.

Have a look at the ATI Driver Wiki link in my signature if you don't have the proprietary driver installed and you want it.   If the wiki doesn't make any sense to you, I'll help walk you through it.

I was able to install the proprietary drivers successfully, and everything appears to work well in GNOME (had to check the no-tearing option) to get flash video playback to work well.

However, it appears that the flash video playback fix doesn't work in dwm--perhaps the proprietary driver treats dwm differently from GNOME.

---

### Post by tulipán on 2012-07-03
hi Qlll, i seem to be having  a similar problem (occasional thermal shutdowns) but i cant make sense of the ATI driver page you suggested. 
this is what i get after (lspci | grep VGA):
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

so i check "integrated motherboard graphics" as step1. but what do i do subsequently?
my laptop is an hp-g62 and have xubuntu 11.04 running on it.
thanx!!!

---

### Post by Redblade20XX on 2012-07-03
Sorry, posted in wrong thread!

-Red

---

### Post by QIII on 2012-07-03
@Loser777

dwm may not play nicely with ATI and Flash.  gdm, kdm and lightdm all seem to work for me.

Flash playback is CPU heavy with ATI because Adobe chose to support GPU acceleration for NVIDIA only.  So ATI is at a disadvantage from the start.

---

