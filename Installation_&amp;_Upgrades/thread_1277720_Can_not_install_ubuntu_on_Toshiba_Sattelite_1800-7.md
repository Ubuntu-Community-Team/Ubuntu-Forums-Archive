---
title: "Can not install ubuntu on Toshiba Sattelite 1800-700"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by chrissk_2 on 2009-09-28
I tried to install jaunty on Toshiba Sattelite 1800-700. It fails to start X but i can not get an error since the system crashes hard. I can not even use Ctrl-Alt-F1 to switch to VT-1.

The video card is a[FONT=monospace] [/FONT]Trident CyberBlade A1i. 

What can i do to finish the installation ?

---

### Post by bumanie on 2009-09-28
You could try the alternate installation cd which is text-based. Or, have you tried booting in safe mode and attempting to fix the graphics problem from there? That is worth trying before going to the effort of downloading the text-based installation cd.

---

### Post by Jackie999 on 2009-09-28
I solved the problem with the answers in this [http://ubuntuforums.org/showthread.php?t=763964](http://ubuntuforums.org/showthread.php?t=763964) thread.
I had to edit the xorg.conf by pasteing the device, monitor and screen sections from that thread to get my entire screen back. I have the trident card as well.

---

### Post by chrissk_2 on 2009-10-02
> **Jackie999 said:**
> I solved the problem with the answers in this [http://ubuntuforums.org/showthread.php?t=763964](http://ubuntuforums.org/showthread.php?t=763964) thread.
I had to edit the xorg.conf by pasteing the device, monitor and screen sections from that thread to get my entire screen back. I have the trident card as well.


Thanks but can you please post your 3 sections here as well ? Because i have already tried several options i found in other posts like "NoPciBurst" and "NoDDC" without any success. 

Thanks in advance

---

