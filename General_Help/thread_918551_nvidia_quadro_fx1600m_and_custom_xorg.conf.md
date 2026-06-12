---
title: "nvidia quadro fx1600m and custom xorg.conf"
date: 2008-09-13
forum: General Help
---

### Post by b4nsh33 on 2008-09-13
Hi, i just received my brand new HP 8710w and installed ubuntu 8.04, so far so good, now im wondering if the default video card detected settings in xorg.conf will get the best performance of this card, i used to have a toshiba latop and by the help of many of this forum i managed to configure X with acceptable performance and with great compiz effects enabled, it worked great, i added the below lines to my previus xorg.conf:

Option "AccelMethod" "EXA"
Option "AccelDFS" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "True"
Option "UseFBDev" "true"
Option "AGPMode" "4"

Section "Extensions"
Option "Composite" "Enable"
EndSection


should i enabled the above xorg.conf's settings in the 8710w too or do i have to trust what ubuntu defaults are guessing?

---

