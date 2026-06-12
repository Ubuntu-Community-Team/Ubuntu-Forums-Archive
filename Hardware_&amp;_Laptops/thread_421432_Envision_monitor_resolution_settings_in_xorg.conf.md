---
title: "Envision monitor resolution settings in xorg.conf"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by jcconnor on 2007-04-24
I have an Envision monitor that is not recognized properly.  Right now the best resolution I can get out of it is 1024X768 but the monitor is capable of 1280X1024.  I would like to increase the settings.  The specs (from the Envision web site) are:

Horizontal - 30k-70kHz
1280X1024/60Hz
17in 

I need to know how and what to change the xorg.conf to be so that the monitor has these higher resolutions.

Any help would be much appreciated!!

Thanks,

John

---

### Post by Surgeon General on 2007-04-24
hey there. what is the Ubuntu release you are using? if it's Feisty then you could, if you have an Intel video chip, try "sudo apt-get install xserver-xorg-video-intel". If it's not Feisty but still an Intel then "sudo apt-get install 915resolution" should do the trick.

---

### Post by jcconnor on 2007-04-24
Thanks for the reply - I'm using Edgy (haven't bitten the bug and gone up to Feisty yet).  I'll try it when I get home.

John

---

### Post by jcconnor on 2007-04-24
That didn't work.  It did give me a blank screen and I had to copy the xorg.conf from my backup.  Maybe someone else has another idea.

John

---

### Post by jcconnor on 2007-04-24
I downloaded and installed the latest NVIDIA driver - with sh (long story on my dumping the NVIDIA going back to the Intel and then reinstalling the NVIDIA - don't ask) and the NVIDIA X Server Settings was able to give me the higher resolutions for my monitor.

Thanks for all the help and I love Ubuntu again!

John

---

