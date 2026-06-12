---
title: "nvidia-glx and i810 dri conflicts"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by sliwowitz on 2007-01-04
Greetings to the Ubuntu community!
I have installed Ubuntu 6.10 on my laptop, which has two graphics cards - an Intel i915 plus nvidia 6600 in an mxm slot. There's a switch to select which one you would like to use on powerup. My problem is, that I don't know how to switch between nvidia and xorg opengl implementations - if I install the nvidia-glx package, I cannot use glx/dri on i810 (while if I do not install it, I will not get glx/dri on nvidia). 
I had Gentoo installed on this machine for one year with both drivers installed. An init script checked lspci to see, which card is present and if the current opengl implementation was invalid, it ran 'eselect opengl' (which is a gentoo tool to select proper glx driver, it changed the libglx.so symlink to the proper one and maybe done some other things).
How can I achieve a similar functionality in Ubuntu?

---

### Post by blu3g3 on 2007-02-10
I hope this can help, i use this script on my vaio laptop with debian. It's similar to the one you say and that uses lspci. It must be loaded at startup, before running X.


libglx.so.1.0.8776 is a copy of libglx contained on nvidia-agp (i think) package.  You must also preserve the one(s) for intel card in order to make the simlink.


VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf-speed /etc/X11/xorg.conf
modprobe drm
modprobe nvidia-agp
rm /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/libGL.so -f
ln -s /usr/lib/xorg/modules/extensions/libglx.so.1.0.8776.bak /usr/lib/xorg/modules/extensions/libglx.so

ln -s /usr/lib/libGL.so.1.0.8776.bak /usr/lib/libGL.so.1
else
modprobe intel-agp
cp -f /etc/X11/xorg.conf-stamina /etc/X11/xorg.conf
rm /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/libGL.so -f
ln -s /usr/lib/xorg/modules/extensions/libglx.so.bak /usr/lib/xorg/modules/extensions/libglx.so
ln -s /usr/lib/libGL.so.1.2.bak /usr/lib/libGL.so.1

fi
#javi gonzalez

---

### Post by QRohlf on 2008-02-23
well, I am using such a script, but I don't know whether I "preserved" the glx for my Intel card. I'm guessing I have not, seeing as I get a 
> Xlib:  extension "GLX" missing on display ":0.0".
on glxinfo.

---

### Post by QRohlf on 2008-02-23
I checked, I do not have these backup files used in the script. Could you please give them to me, so that I can use them!
Thanks!

---

### Post by sliwowitz on 2008-02-24
Unisntall the nvidia-glx package, that should give you the files back. Then you can copy them to somewhere safe a install the nvidia-glx again - this will give you the nvidia files.

---

