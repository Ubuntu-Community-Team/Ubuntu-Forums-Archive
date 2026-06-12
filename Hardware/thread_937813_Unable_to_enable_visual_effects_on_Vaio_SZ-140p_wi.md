---
title: "Unable to enable visual effects on Vaio SZ-140p with onboard video..."
date: 2008-10-04
forum: Hardware
---

### Post by m_ajmera on 2008-10-04
I have installed Ubuntu 8.04 on my SZ-VGN140p. The laptop comes with 2 video cards (nVidia 7400 and onboard video). I got them both working with the a script that switches the Xorg.conf file based on whether I have selected speed or stamina setting on my laptop.

My problem is that on the stamina settings I am not able to enable "Visual Effects". 
Is there a way to fix this?
Could it be that my onboard video is not recognized correctly and is not being used completely?

I am newbie to Linux so please bear with me.

Thanks a lot
Mayank

---

### Post by m_ajmera on 2008-10-05
I think I found out what the problem is...

My onboard video is 945gm but I am not using the Intel Driver. Unfortunately when I installed the nVidia driver, it seems to have done something irreversible to the libraries used by the Intel Driver. 

Re-installing ubuntu allowed me to set the device to "intel" in the xorg.conf and I was able to enable Visual Effects now. I haven't booted up with the nVidia GPU yet.

---

