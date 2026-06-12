---
title: "I can't log in"
date: 2009-10-09
forum: Hardware
---

### Post by FelixS on 2009-10-09
I have installed Ubuntu 9.04 in a reasonable old computer (7 years old). This works (first) with no issue or problem. Then I have actualized it with the Actualizations Manager. All OK. Then I tried to use some applications that use 3D, and a error message appears, saying that I don´t have a OpenGl supporting video card. I believed that it happened because there was a missing appropriate driver for my video card (an ATI Radeon 7000 series). I have installed the right drivers and then restart the computer. I have seen the computer starting normally, but after the Ubuntu logo, and the loading bar appears, the login window doesn't appears. Now, !what can I do?¡   :mad:

---

### Post by overdrank on 2009-10-09
> **FelixS said:**
> I have installed Ubuntu 9.04 in a reasonable old computer (7 years old). This works (first) with no issue or problem. Then I have actualized it with the Actualizations Manager. All OK. Then I tried to use some applications that use 3D, and a error message appears, saying that I don´t have a OpenGl supporting video card. I believed that it happened because there was a missing appropriate driver for my video card (an ATI Radeon 7000 series). I have installed the right drivers and then restart the computer. I have seen the computer starting normally, but after the Ubuntu logo, and the loading bar appears, the login window doesn't appears. Now, !what can I do?¡   :mad:

Hi and you may try and use the xfix option when booting into recovery mode to correct the graphical issues.
Recovery mode is usually the the second choice when booting from the grub. Then you should be given 4 option with xfix being the last. After completing xfix you should be given the choice to boot normally and hopefully this will get you to the desktop. :)

---

### Post by FelixS on 2009-10-10
Ok, thanks, I will try it. :KS

---

### Post by FelixS on 2009-10-12
I did what you said to me, but the problem continued. But do not worry, I get part of the solution in this forum:[INDENT][http://ubuntuforums.org/showthread.php?t=1134841](http://ubuntuforums.org/showthread.php?t=1134841)
[/INDENT]I get in the recovery mode, then selected the netroot option, and typed this:[INDENT][INDENT][COLOR=Red]sudo apt-get remove --purge xorg-driver-fglrx[/COLOR]
[/INDENT][/INDENT]Then it asked me if a desire to continue. I continued. Then I reboot the computer, and it started properly. But now, I want to complete the solution. I need the stable driver for my ATI Radeon 7000 series to work using 3D. Thanks for your attention.

---

