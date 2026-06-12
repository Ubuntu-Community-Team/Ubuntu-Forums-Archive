---
title: "Problem installing nVidia driver in mythbuntu 8.04.1"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by sperwer on 2009-07-24
Update:
Since yesterday i have switched to mythbuntu 8.04.1 32 bit. It got me closer but i still have driver installing problem.
I can install the driver using this method:
* shift to terminal using CTRL-ALT-F1
* Log in
* sudo /etc/init.d/gdm stop
* sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run
* sudo /etc/init.d/gdm start(when i do this xserver starts with the nvidia driver loaded, however it only last until next reboot and have to do the steps again.

Hope for some help
Sperwer


..Hi i have tried to to install nvidia 185.8.14 driver on mythbuntu 8.04.1 (64 not sure)
However it doesn't seem to work.
After installation of driver and reboot i get message that graphic adapter and display cant be found.

If i try to start nvidia xserver settings i get this message:
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

I did run nvidia-xconfig, however no change. I have then installed the proprietary driver, whis resluted in blank screen after reboot.

Any suggestions ar appreciated.

Sperwer

---

