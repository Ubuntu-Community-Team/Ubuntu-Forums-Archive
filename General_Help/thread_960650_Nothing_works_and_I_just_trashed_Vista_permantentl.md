---
title: "Nothing works and I just trashed Vista permantently."
date: 2008-10-27
forum: General Help
---

### Post by khopek on 2008-10-27
I install Ubuntu to dual boot with Vista yesterday, everything worked except wireless, and I just had to enable my Nvidia graphic card. So I decided to trash Vista, and the restore partition that came on my drive.

I did a fresh install of Ubuntu, and now nothing work:

1. I get a warning saying my computer is in 'low graphics mode'
2. I have no proprietary drivers showing for my Nvidia card, or my Atheros 3. Wireless Card (which I did have on a dual boot install) AND I have no d. other drivers for either of these. 
4. I can't find any information that works.
5. The volume controls on my laptop no longer work. Although I get sound, Linux thinks the volume is muted.

System Specs:
HP Compaq Presario v6000 or v6719nr (there's two different number on my laptop)
-AMD64 Athlon X2
Nvidia GeForce 7150M (rev a2) (according to Terminal)
Atheros AR242x 802.11abg Wireless PCI Express Adapter (rev 01) (according to Terminal)

I am a newbie and this experience has been SO frustrating. Not enough to cause me to go back to Windows though.:)

---

### Post by Doji on 2008-10-27
If the install went fine the first time, I see no reason why anything should be different the second time. Make sure your partitions aren't messed up and give the install another shot. That'll probably be easier than trying to troubleshoot the problems on your failed install. Good luck.

---

### Post by Jense on 2008-10-27
Hi,
there is not much information. I assume your system does boot into linux and tries to start the x-server (gui). And there you recive the low grafics warning?
I assume you are running hardy?
If so, when you get the "low grafics warning" try to do> Crtl+Alt+F4
This should bring you to a terminal loging. Loging and try to edit your xorg.conf
> sudo nano /etc/X11/xorg.conf
In the device section where it says something about NVIDIA find the line driver and change it so it shows> Driver "nvidia"

Then save and exit > Ctrl+x
This should make the xserver load the generic driver and hopefully you will have working grafics after that.

Hope this helps, good luck

---

