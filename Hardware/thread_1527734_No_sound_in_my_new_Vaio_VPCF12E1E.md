---
title: "No sound in my new Vaio VPCF12E1E"
date: 2010-07-09
forum: Hardware
---

### Post by Josemsar on 2010-07-09
Hi to all i am very noob so sorry if i don't know how should i start 


First of all thanks to thanks to it i have fixed the problems with the video card and touchpad, now y need sound, y dont know what shuld i do, uing headphones i heard perfectly but, thoug the speakers nothing, what should i do?

Thanls

---

### Post by lidex on 2010-07-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Josemsar on 2010-07-10
```
josemsar@Portatil:~$ uname -a
Linux Portatil 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
josemsar@Portatil:~$ aplay -l
aplay: device_list:223: no se encontraron tarjetas de sonido...
josemsar@Portatil:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
josemsar@Portatil:~$ head -n l /proc/asound/cars*/codec#*
head: l: el número de líneas no es válido
josemsar@Portatil:~$ head -n 1 /proc/asound/card*/codec#*
head: no se puede abrir «/proc/asound/card*/codec#*» para lectura: No existe el fichero ó directorio
josemsar@Portatil:~$ ^C
josemsar@Portatil:~$ 
```

Sorry but i think i deleted the driver with some test...

Thanks by the help

Its a SONY VAIO F VPCF12E1E

---

### Post by lidex on 2010-07-10
Try re-installing alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**

---

### Post by Josemsar on 2010-07-10
Nothing, it hasent detected the Sound card, but, when I installed ubuntu, it was recognized and the headphones worked, but the Laptop speakers didn't


What more should I do?

---

### Post by lidex on 2010-07-10
Did you re-install alsa? 
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by soapytheclown on 2010-07-12
try this, it fixed the lack of sound on my sony vaio vpcec1s1e

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa/ubuntu
sudo aptitude update
sudo aptitude install linux-alsa-driver-modules-$(uname -r) linux-backports-modules-alsa-$(uname -r)-

i think that last line can be replaced with this otherwise you'll need to keep installing them everytime u get a kernel update:

sudo aptitude install linux-backports-modules-alsa-lucid-generic

---

