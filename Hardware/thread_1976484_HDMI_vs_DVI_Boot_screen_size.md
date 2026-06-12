---
title: "HDMI vs DVI Boot screen size"
date: 2012-05-08
forum: Hardware
---

### Post by makitso on 2012-05-08
Have an Nvidia GForce 520 in a 12.04 system.  Originally, I had a DVI cable from it to my ViewSonic with a HDMI converted -- the monitor only supports HDMI.  Today, I replaced the DVI with an HDMI cable and now the grub menu is low resolution as is the Ubuntu loading graphic.  Once it gets to the login its fine.   Its no big thing but I would like to know why and if there is an easy fix?  I am running 1920 x 1080.

---

### Post by darth62969 on 2012-05-23
the issue is scaling/hardware. 
the explanation:
the monitor, or the gpu (like mine) will scale back the size of the BIOS screen or the preliminary boot screens until it gets to the OS. i run windows and i actually experience this "issue" with the BIOS screen all the time. when i boot my system the BIOS screen is all ways under scaled on my dell monitor. this is a hardware "issue" that you don't really have any control over. and it varies with from monitor to monitor. for example i actually have had 2 dell monitors a CRT that ran VGA and a LCD that runs without adapters DVI and VGA. mine came with a HDMI adapter and since i prefer HDMI or DVI over VGA i used the HDMI adapter and a spare HDMI cable i had and ran it. i experienced this issue and only with the HDMI.

---

