---
title: "HW Accel with newer Ubuntu + Nvidia Geforce 440go"
date: 2011-12-24
forum: Hardware
---

### Post by Brinstar on 2011-12-24
I am helping a relative upgrade Ubuntu 8.04 to a version that has full hardware acceleration with the official Nvidia drivers for the hardware in question.

Currently 8.04 is working fine, but there are some things that aren't available in synaptic due to it no longer being supported. The reason I still use 8.04 on this laptop (Dell Latitude C840) is because the version of Xorg (7.3) is the last version that is compatible with the only drivers (96.xx) that work with this nvidia card (Geforce4 440go).

I want to upgrade it to 10.04 or 11.10, but i'm aware that the old 96.xx driver is not supported by the newer X-server 1.9 (or whatever the version number happens to be) so i haven't done this until now. 

I don't want to use the nv driver, as that has never provided adequate acceleration for gaming.

Is there any way i can upgrade this laptop to a newer, supported version of Ubuntu and still get full hardware acceleration with any relevant Nvidia drivers?

edit: i wasn't aware of this, found it after some googling. it looks as if the newer Ubuntus work with 96.xx?

[http://www.nvnews.net/vbulletin/showthread.php?p=2341157](http://www.nvnews.net/vbulletin/showthread.php?p=2341157)

not sure if this will work, but it's worth a try

---

### Post by MrSpike16 on 2011-12-24
The Nvidia-96 drivers are in the Ubuntu 10.04 and 11.10 repositories, supported by Canonical, so you are good to go.

By the way, Nvidia is still updating this driver when new X server versions comes out.

---

### Post by Brinstar on 2011-12-25
thanks yeah i finally did get that sorted, forgot to update here. i got a black screen after installing the 96 drivers (as expected) and i fixed it using the method i used previously to fix this issue :

[http://ubuntuforums.org/showthread.php?p=9771821#post9771821](http://ubuntuforums.org/showthread.php?p=9771821#post9771821)

and it's good to know nvidia will continue supporting the older devices, thats uncommon for a big company.

---

