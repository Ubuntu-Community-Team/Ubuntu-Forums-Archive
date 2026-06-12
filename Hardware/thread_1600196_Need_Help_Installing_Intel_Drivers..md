---
title: "Need Help Installing Intel Drivers."
date: 2010-10-18
forum: Hardware
---

### Post by B00MB0X on 2010-10-18
Hi all, Im having trouble setting up my graphics driver. i have ran lspci | grep VGA
and got "VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)" the driver was working fine until i decided to install the manufacturer driver to get better results in WoW and other games, and to have a bit higher res. according to my computers manufacturer i  had an nvidia (-_- not true) so after rebooting the system (after instaling the nvidia driver) i had no display. i deleted xorg.conf to gain the display back. but now i have very minimal graphic options. my solution as far as i know is: install the correct driver (intel) so i downloaded it but it only runs under 2.4.x kernels
and im running 2.6.32-25-generic (all this information i got from the installer) so i figured download the old one from packages.ubuntu.com i found the right one and it wont install i get this error "Error: Dependency is not satisfiable: initrd-tools (>= 0.1.48)" anyone know how i can get aronud al this and just install my intel driver? also. i am almost positive im on the latest ubuntu but not sure

---

### Post by efflandt on 2010-10-19
I believe you are running Ubuntu 10.04 since 10.10 uses a different kernel (higher version).

Did you uninstall the nvidia driver, or at least remove its xorg.conf?

---

### Post by cascade9 on 2010-10-19
You dont need to manually install the intel video drivers. The drivers should be all open source (xserver-xorg-video-intel). 

> **B00MB0X said:**
>  according to my computers manufacturer i had an nvidia (-_- not true) so after rebooting the system (after instaling the nvidia driver) i had no display. 

What model computer do you have?

---

### Post by mastablasta on 2010-10-19
it could be that you have 2 graphics cards. an onboard (enabeled) intel and a disabled nVidia card.

---

### Post by B00MB0X on 2010-10-19
The probelm was i wanted better results from the games i ran.(via wine) i figured a driver upgreade would be better vs the driver ubuntu came with so theres no way to install the intel drivers?

---

### Post by B00MB0X on 2010-10-19
> **cascade9 said:**
> You dont need to manually install the intel video drivers. The drivers should be all open source (xserver-xorg-video-intel). 



What model computer do you have?
  i have a HP dc 5000 sff

---

### Post by B00MB0X on 2010-10-19
Ive resolved the issue of the display.. but now im back to square one.. the games and stuff look horrible.  is hardware acceleration possible? I know i sound stborn but these games ran fine and looked great under my other Linux PC (the driver was installed on that one automatically , i mean its recognized) my guess once again is to install the driver to get the best performance sorry for being such a hassle anyone have any ideas on how i would go about that?:confused:

---

### Post by cascade9 on 2010-10-20
According to HP, that system didnt comewith a video card- 

[http://h18000.www1.hp.com/products/quickspecs/11876_na/11876_na.HTML](http://h18000.www1.hp.com/products/quickspecs/11876_na/11876_na.HTML)

You could probably install one, but finding a half height PCI card isnt easy. 

> **B00MB0X said:**
> Ive resolved the issue of the display.. but now im back to square one.. the games and stuff look horrible.  is hardware acceleration possible? I know i sound stborn but these games ran fine and looked great under my other Linux PC (the driver was installed on that one automatically , i mean its recognized) my guess once again is to install the driver to get the best performance sorry for being such a hassle anyone have any ideas on how i would go about that?:confused:

Thats probably more about how horrible the intel video chips are (Intel Extreme Graphics 2 is slower than older ATI /nVidia cards). 

I'd guess that your other linux computer has an ATI or nVidia card (probably nvidia).

---

### Post by B00MB0X on 2010-10-20
So theres no way to use the existing card and get better performance from it?

---

### Post by cascade9 on 2010-10-21
Using the newest drivers might help. 

You would need to get them from a PPA (I'll see if I can find some how-to for that) 

[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/)  ****

---

### Post by B00MB0X on 2010-10-22
> **cascade9 said:**
> Using the newest drivers might help. 

You would need to get them from a PPA (I'll see if I can find some how-to for that) 

[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/)  

thanks that would really help :)

---

