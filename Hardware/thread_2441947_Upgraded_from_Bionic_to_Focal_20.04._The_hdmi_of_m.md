---
title: "Upgraded from Bionic to Focal 20.04. The hdmi of my Asus GL552VW Laptop hdmi Fails"
date: 2020-04-28
forum: Hardware
---

### Post by mvcial on 2020-04-28
Good Morning

After updating my laptop, when I connect the external monitor via hdmi, it turns on and off continuously, it is impossible to work with said monitor, this did not happen with version 18.04.

I don't know what to look at, could you help me?Good Morning

After updating my laptop, when I connect the external monitor via hdmi, it turns on and off continuously, it is impossible to work with said monitor, this did not happen with version 18.04.

I don't know what to look at, could you help me?

my graphic card information

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd0000139Bsv00001043sd00001C5Dbc03sc02i00
vendor   : NVIDIA Corporation
model    : GM107M [GeForce GTX 960M]
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-440 - distro non-free recommended
driver   : nvidia-driver-435 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin


I have the recommended driver installed.

---

### Post by mörgæs on 2020-04-28
If you want 20.04 then do a fresh install, not an upgrade. 

Be aware that the [release notes]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes") mention some problems for Nvidia.

---

### Post by mvcial on 2020-04-28
the update has not given any problem, and the laptop screen has no problem, right now I can not do a fresh installation

---

### Post by SeijiSensei on 2020-04-28
Have you tried the open-source nouveau driver? Does it lack features you need?

I'm running 20.04 on a laptop with a GF108M [GeForce GT 555M] and NVIDIA 390.132. Haven't had any problems.

---

### Post by mvcial on 2020-04-28
If I have tried it and although it blinks less, it still does, i'll try to use this NVIDIA 390.132.

---

### Post by mvcial on 2020-04-29
I have tried with the version of the driver that you tell me and it still fails.

Thank you

---

### Post by mvcial on 2020-05-19
I have done a clean installation but the same thing continues, can someone help me

---

### Post by ajgreeny on 2020-05-19
Can you try another HDMI cable as they are renowned for being a bit problematical according to many users.

---

### Post by mvcial on 2020-11-16
I have tried with several hdmi cables and everything remains the same

---

