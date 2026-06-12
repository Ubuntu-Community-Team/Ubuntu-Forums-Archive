---
title: "Problems with ATI RAGE video card"
date: 2009-03-02
forum: Hardware
---

### Post by pentium_3 on 2009-03-02
I just recently wiped the Windows XP installation on my brother's (very old) computer and installed Xubuntu. So far, everything works just fine, the exception being the Video Card. The Card is an ATI RAGE 128 GL plugged into the AGP slot. It has 32 MB of dedicated video memory. 

It seems as if Xubuntu could not find a specific Driver for the ATI card, I think it is just using a generic VGA driver. As a result, there are several problems. 3D applications don't quite work well, and will often freeze or flicker. Also, on boot up, I cannot see the splash screen- my monitor displays a message reading "Input signal out of range". Though relatively minor problems, they are annoying and I would like to get them fixed. I'm new to Linux (primarily use WinXP and Mac OS 9), so if anyone could provide me with a solution and instructions on how to install any driver or drivers it would be great. Thanks!

---

### Post by 00b00nt00 on 2009-03-03
I have a Rage Mobility chipset on my Ubuntu computer, and it works out-of-the-box. It sounds like something went wrong somewhere in the installation - look in the xorg log files for any errors.

Don't expect things like Compiz to work, though.

---

