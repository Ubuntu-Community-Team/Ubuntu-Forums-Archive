---
title: "Low resolution issue. ¡Help! (10.04 on Lenovo z470) Thank You"
date: 2012-01-20
forum: Hardware
---

### Post by Bbeto on 2012-01-20
I don't know if it's bad luck or something else but i haven't been able to install a nice and smooth linux OS in this laptop Lenovo z470 (i've only tried 10.04 and 11.10?

I've just installed 10.04 cuz 11.10 was extremely unstable for my laptop. Still, i have several issues after installation (battery drain, brightness keys and low resolution wich is the first i want to fix)

When i boot ubuntu the resolution of my screen gets low (1024x768) when the max resolution, which works in windows, is 1366x768.
I've tried creating a xorg.conf file but didn't work (maybe because i was not sure about all the specs i wrote on it). 

People, i really need to get ubuntu to work, madness is already knocking on my door. Pleaaase help, i'm quite newbie and i want to learn more about linux but first i need a fully functional ubuntu!!!

btw, my graphics chip? is an intel 0116.
Alberto

---

### Post by Lekensteyn on 2012-01-21
You usually do not need /etc/X11/xorg.conf, so remove it. Do you even have the issue on a Live CD?

---

### Post by Bbeto on 2012-01-21
> **Lekensteyn said:**
> You usually do not need /etc/X11/xorg.conf, so remove it. Do you even have the issue on a Live CD?
Yes, actually the resolution was low since i run the livecd (USB stick) before installation. I already removed the xorg.conf since it caused me trouble with the booting.
It has anything to do with xserver-xorg-video-intel? cause today i installed that upgrade and nothing good happened.
Thank you for answering.

---

### Post by Lekensteyn on 2012-01-22
Does your model have a NVIDIA chip? Googling for it reveals that a Lenovo Z470 has a NVIDIA GT 520M chip.

In that case, you have an Optimus laptop, see [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969). Basically, you have to install bumblebee-nvidia which will configure paths in such a way that it does not conflict with the Intel card.

---

### Post by Bbeto on 2012-01-22
> **Lekensteyn said:**
> Does your model have a NVIDIA chip? Googling for it reveals that a Lenovo Z470 has a NVIDIA GT 520M chip.

In that case, you have an Optimus laptop, see [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969). Basically, you have to install bumblebee-nvidia which will configure paths in such a way that it does not conflict with the Intel card.
No, my specific model of z470 comes without Nvidia chip. I only have the Intel HD graphics family.

I don't know if this helps but, another detail i noticed is that with ubuntu 11.10 the resolution works fine.

---

### Post by Lekensteyn on 2012-01-22
Recent hardware are better supported by the latest Ubuntu version. If you want to use 10.04, post your /var/log/Xorg.0.log and /var/log/kern.log on [http://paste.ubuntu.com](http://paste.ubuntu.com) and post the links here.

---

### Post by hesabb on 2012-03-10
hey

has  anyone fixed this issue with z470?
I have z470 with optimus and I have set my bios switch to use optimus (nvidia enabled), i have also bumblebee installed,

problem is that i still have really low resolution, should I run  x server with optirun command? how?

how to get back my optimum resolution? I am using 10.04 ubuntu

---

### Post by Lekensteyn on 2012-03-11
> **hesabb said:**
> hey

has  anyone fixed this issue with z470?
I have z470 with optimus and I have set my bios switch to use optimus (nvidia enabled), i have also bumblebee installed,

problem is that i still have really low resolution, should I run  x server with optirun command? how?

how to get back my optimum resolution? I am using 10.04 ubuntu
Have a look at [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969). You most likely have a /etc/X11/xorg.conf file present that should be removed. Reboot after doing so.

---

### Post by hesabb on 2012-03-15
> **Lekensteyn said:**
> Have a look at [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969). You most likely have a /etc/X11/xorg.conf file present that should be removed. Reboot after doing so.

I checked! there is no directory called X11 in /etc :(
I have disabled my nvidia card from bios! system only sees one card at the moment! I just need my resolution to be fixed ( I guess I should give up on 3d effects)

even with only my intel HD 3000 vga card enabled, ubuntu 10.04 refuses to recognize it and my resolution is low as hell

how can I setup my intel now? any suggestions?

---

### Post by Lekensteyn on 2012-03-16
Remove the nvidia-current package or install Bumblebee (see previous link) to fix resolution issues.

---

