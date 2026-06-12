---
title: "Ati 3d Acceleration"
date: 2010-06-01
forum: Hardware
---

### Post by Abdujaparov on 2010-06-01
Hi,
I installed ubuntu 10.04 64bit but I have problem with 3d acceleration.
I cannot install the ati driver because it support the old version of xorg. I read a guide but I have problem.

My video card is:
> 
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600]


That is the output of this command:
lspci | grep VGA

I tried to launch glxinfo but I receive this message:
> 
angelo@angelo-desktop:~$ glxinfo 
name of display: :0.0
Segmentation fault


The file /etc/X11/xorg.conf is completly empty.
How can I solve?
Thanks, bye bye.

---

### Post by Dharma-station on 2010-06-01
Unfortunately Catalyst, the official ATI driver, doesn't appear to be compatible with your video card. See here:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.19&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.19&lang=English)

Your only current option is to use the open source driver "xf86-video-ati". It should be enabled by default in Ubuntu but if its not you can apt-get it.
It's really quite a mature driver now-a-days. Perhaps give it a whirl? If you're doing some intense gaming it may be time for an upgrade :(

Also, glxinfo is part of the "mesa-utils" package.

Hope that helps!

---

### Post by khelben1979 on 2010-06-01
Using an older version of Ubuntu is also an alternative if you intend to use Ubuntu for heavy Linux gaming. Then you can keep on using the prop. driver from ATi.

Otherwise, go get a newer graphics card.

---

