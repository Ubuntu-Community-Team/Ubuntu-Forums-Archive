---
title: "Desktop Effects Don't Work in Hardy Virtual Box"
date: 2008-08-18
forum: General Help
---

### Post by seismicmike on 2008-08-18
I am running Ubuntu 8.04 Hardy Herron inside Virtual Box on my Windows XP laptop. I have a couple issues:

1) Desktop effects don't work. I can't enable even the normal ones, much less run Compiz Fusion. I would very much like to get the cube and all the glitz going.

2) Screen resolution is limited to 800 X 600

3) I can only use the laptop's wired ethernet networking... Can't use wireless, even though to my understanding the OS inside the virtual box shouldn't know the difference.

I know neither of these are issues with my hardware because on this same computer I also have hardy installed as a dual boot (using Wubi) and have Compiz, 1280 X 800 screen resolution and wireless working.

Any insight would be wonderful. Thanks.

---

### Post by tuxxy on 2008-08-18
Desktop effects will not work in a virtual environment, my advice install ubuntu and run XP in virtual much better :)

---

### Post by seismicmike on 2008-08-19
> **tuxxy said:**
> Desktop effects will not work in a virtual environment, my advice install ubuntu and run XP in virtual much better :)

Well fooey :)

Thanks for the insight. I've debated doing the switcheroo, but I don't have all the install discs for my software and am rather entrenched right now, but I may end up doing it in the future. That is my ideal system though...

---

### Post by wahoobob on 2008-08-19
You might try a dual boot system so you have the best Ubuntu and the best XP (such as it is) you can get.  Later when you can do without XP you can eliminate that partition or move the few things you want to a VB.

---

### Post by Mgiacchetti on 2008-08-20
and remember, if you go ubuntu, with virtualbox inside for xp, 1.6.2-1.6.4 virtualbox guest additions have a problem, basically they are broke.

[go here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") to get the latest version of Virtualbox for your distro (btw ose sucks, xVM is much better) then go [here]("http://www.virtualbox.de/download/1.6.0/") and grab the iso, use this instead of the 1.6.>0 guest additions, as these will work where the newer ones dont.

Download the iso to your desktop then open terminal and do the following:
```

cd Desktop
sudo cp /usr/share/virtualbox/VBoxGuestAdditions.iso /usr/share/virtualbox/VBoxGuestAdditions.iso.original 
sudo rm /usr/share/virtualbox/VBoxGuestAdditions.iso
sudo cp -T VBoxGuestAdditions_1.6.0.iso /usr/share/virtualbox/VBoxGuestAdditions.iso
rm VBoxGuestAdditions_1.6.0.iso

```

---

