---
title: "Intrepid freezing"
date: 2008-11-20
forum: Hardware
---

### Post by tjd_98 on 2008-11-20
Ok i'm fairly new to linux but have had no problems with ubuntu until now. I am running Kubuntu 8.10(gnome is slower on my laptop)on an Acer Aspire 3620. My problem is I think with my graphics card, built in Intel 915GML. Installation went fine, only problem I had to partition manually. After I boot my laptop and log in I can't do anything. Just to get my cursor over the Kmenu takes 5-10 min then I can't get the kmenu open. The other problem, which is why I think it may be a graphics card problem, is that my screen seems to flicker. I found some info about the screen flicker but all the solutions need me to go into the Kmenu>system>display... which I can't do.

This is what i've done so far: ran memtest...fine
checked file system...fine
tried to boot to failsafe...received error about xserver (don't have exact wording at the moment)
Can boot into recovery and use console.
tried editing xorg.conf with some info I found about the screen flicker...no help.

anyone got any ideas. I really don't want to have to reinstall an older version (can't get hardy to partition so I have to go back to edgy then upgrade)

Thanks for any help

Tyler

---

### Post by tjd_98 on 2008-11-21
New discovery. The hdd indicator light is on all the time after login. I have no problems getting to the cli through the recovery mode. Not sure if this has to do with the graphics problem but if I can get it to run I should be able to fix the flicker by changing the refresh rate/resolution.

---

### Post by tjd_98 on 2008-11-21
Problem solved. Not sure what changed but I reinstalled (again) in safe graphics mode and it works fine

---

