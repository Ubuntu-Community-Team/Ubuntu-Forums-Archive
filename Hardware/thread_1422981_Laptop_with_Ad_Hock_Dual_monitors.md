---
title: "Laptop with Ad Hock Dual monitors"
date: 2010-03-06
forum: Hardware
---

### Post by Morganvd on 2010-03-06
Hi I'm wondering if anyone could help. I have a HP Elitebook 8730w with Nvidia Quadro FX2700 gfx card. I also have a PView external LCD screen that I connect up at home.

Im still very new to Ubuntu and have searched the forums and web upside down to find a solution to my problem. I wrote a script to check if the laptop is on its own it should use one xorf.conf and then the external is pluged in to use both. 

I followed this guide [http://sernaonubuntu.wikidot.com/multiple-monitors](http://sernaonubuntu.wikidot.com/multiple-monitors)

I have noticed the following using lspci
```
black@morgan-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G94M [Quadro FX 2700M] (rev a1)

```

Using sudo ddcprobe
```
black@morgan-laptop:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: G94 Board - 0610501B Chip Rev
memory: 14336kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

```

The script im using is the same as the one in the link

```
# determine whether an external display is attached
if /usr/sbin/ddcprobe | grep "monitorname"; then
echo "External Display attached."
# set external display as exclusive primary
cp /etc/X11/xorg.twoscreens.prod /etc/X11/xorg.conf
else
echo "Using built-in LCD."
# set build-in LCD as exclusive primary display
cp /etc/X11/xorg.justlaptop.prod /etc/X11/xorg.conf
fi
```

I have also told the script to run before before the xorg starts up like the guide said

Any help would be really appreciated. Currently I have to login manually copy xorg file as I loging and reboot.

---

### Post by Morganvd on 2010-03-06
Anyone?

---

### Post by Morganvd on 2010-03-09
Ok now im really confused. Clean install of Ubuntu 9.10 with built in nv driver and the fn key chooses between screens. I have a HP so the fn key plus f4 changes between presentation and duel monitors. The min I install the Nvidia Drivers from the repository it does not work.

Any advice would be greatly appreciated

---

