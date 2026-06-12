---
title: "nVidia 6200 graphics card resolution help"
date: 2008-09-24
forum: Hardware
---

### Post by JCamps on 2008-09-24
So I'm new to Ubuntu, it's been heavily recommended by a few of my friends, so I'm not sure if I'm missing something or what.
Basically, I've got an nVidia geforce 6200 graphics card and Ubuntu 8.04 LTS, now I downloaded the restricted nvidia drivers, but now the highest resolution I can have is 640x480. There has to be some way that I can make this higher, I was using windows and my resolution is 1280x1024. If it means anything, I installed ubuntu inside windows. Help?

---

### Post by JCamps on 2008-09-24
Anyone have any suggestions?

---

### Post by Crafty Kisses on 2008-09-24
You can try reconfiguring X:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by JCamps on 2008-09-24
What'd that accomplish? It seems like it just dealt with my keyboard.

---

### Post by overdrank on 2008-09-24
> **JCamps said:**
> So I'm new to Ubuntu, it's been heavily recommended by a few of my friends, so I'm not sure if I'm missing something or what.
Basically, I've got an nVidia geforce 6200 graphics card and Ubuntu 8.04 LTS, now I downloaded the restricted nvidia drivers, but now the highest resolution I can have is 640x480. There has to be some way that I can make this higher, I was using windows and my resolution is 1280x1024. If it means anything, I installed ubuntu inside windows. Help?

Hi yes that command has changed some with Hardy. If you have the drivers enabled then you may try and install the nvidia-settings via synaptic manager. Then you can use the command with alt, F2 keys ```
gksu nvidia-settings
``` and adjust your resolution there. If you are unable then you may use this command ```
gksu displayconfig-gtk
``` to setup your monitor. If all fails above then boot into recovery mode which is usually the seconded choice from booting the grub. Then use the xfix option to correct your graphics. :)

---

### Post by nixsy9 on 2009-05-05
thanks thats sorted my dual view problem with my 6200 card. I am new to ubuntu and still learning

Nix

---

