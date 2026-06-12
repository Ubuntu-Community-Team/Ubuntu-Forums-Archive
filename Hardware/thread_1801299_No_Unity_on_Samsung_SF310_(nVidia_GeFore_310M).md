---
title: "No Unity on Samsung SF310 (nVidia GeFore 310M)"
date: 2011-07-10
forum: Hardware
---

### Post by f_padia on 2011-07-10
I have a Samsung SF310 laptop which has an nVidia Geforce 310M graphics card built in. When I install the proprietary nVidia driver from 'additional drivers' it says my graphics card is not suitable for Unity. I find this quite amazing since its a very new laptop. When I remove the nvidia driver Unity runs ok.
However, it seems that without the nvidia driver I cant play games through wine  because the graphics card isnt good enough. After investigating, it appears as though disabling the nvidia driver causes the system to use the Intel graphics chip on the motherboard. This is apparently ok to run Unity but not for games.

I followed the instructions on this thread:
[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)
and installed the nvidia 173 driver from synaptic and added UNITY_FORCE_START=1 to /etc/environment but this didnt work either.
So then I tried to install the nouveau driver in Synaptic (see screenshot) but for some reason this isnt showing up in additional drivers.
So my questions are:
(1) Does anyone know why a newish graphics card isnt able to run unity while an onbaord graphics chip is?
(2) How do I install the nouveau driver?
Thanks

---

### Post by f_padia on 2011-07-11
does no one else have a graphics card that is incompatible with unity?? unbelievable? why did I choose this laptop???!!

---

### Post by lightpurpledye on 2011-08-28
I have the same laptop, and while Unity was working before on 11.04, I have just reinstalled from CD to find the same symptoms as you. I have not found a solution, sorry.

---

