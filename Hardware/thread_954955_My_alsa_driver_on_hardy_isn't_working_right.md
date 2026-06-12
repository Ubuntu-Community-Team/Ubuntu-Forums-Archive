---
title: "My alsa driver on hardy isn't working right"
date: 2008-10-21
forum: Hardware
---

### Post by Black Blade on 2008-10-21
I'm using a Toshiba Satillite A135-S457 and when I plug my headphones in sound comes out of the headphones and the speakers can anyone help me?
My sound card is:
Card: HDA Intel 
Chip: Realtek ALC861-VD

---

### Post by teaker1s on 2008-10-21
hda -intel there have been various issues and threads regarding this:- more often than not adding computer make to alsa as a model config works try auto,basic or toshiba
more here 
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by Black Blade on 2008-10-21
I don't understand what this site wants me to do could you explain more?

---

### Post by magusxp on 2008-10-21
Install the linuxant driver
I had same problem

---

### Post by Black Blade on 2008-10-21
Is that in the package manager?

---

### Post by magusxp on 2008-10-21
yes its in synaptic... if not
just type linuxant alsa driver

---

### Post by teaker1s on 2008-10-21
Terminal
```
sudo gedit /etc/modprobe.d/alsa-base
```

Then paste the following line at the end of the file (change MODEL with the type of sound card's [COLOR="Sienna"]model[/COLOR]: try basic or auto or toshiba

```
options snd-hda-intel model=[COLOR="Sienna"]MODEL[/COLOR]
```

save and reboot

---

### Post by Black Blade on 2008-10-21
Neither of those worked and the driver thing made all sound go away.

---

### Post by teaker1s on 2008-10-22
Use Synaptic or apt-get to remove the linuxant driver and remove the line I said to try. it sounds like the version of alsa you are using is old:-are you using ubuntu 6.06lts?

---

### Post by Black Blade on 2008-10-22
Im using 1.0.16 for the base.

---

### Post by teaker1s on 2008-10-24
you problem is the build of alsa and your hda-intel sound. I have personally experienced this:- building alsa from source or dist upgrade will cure it.

---

