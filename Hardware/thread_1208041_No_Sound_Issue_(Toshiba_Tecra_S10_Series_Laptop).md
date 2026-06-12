---
title: "No Sound Issue (Toshiba Tecra S10 Series Laptop)"
date: 2009-07-08
forum: Hardware
---

### Post by tamerucar on 2009-07-08
Hi All,

I have a Toshiba Tecra S10-11A laptop. I decided to install Ubuntu 9.04. I'm experiencing a problem with my audio driver. I cannot get any sound from my laptop.

I got the following info:

```
asoundconf list
```
returns

```
Names of available sound cards:
Intel

```

after that:

```
lspci | grep -i audio
```
returns

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

and lastly:

```
cat /proc/asound/card0/codec#* | grep Codec
```
gives me this result

```
Codec: Realtek ALC268
Codec: LSI ID 1040

```


According to these info, how can I make my sound card work?  :?

Thanks for your help...

---

### Post by tamerucar on 2009-07-09
Any idea :icon_frown:

---

### Post by tamerucar on 2009-07-09
Hi, my problem is solved by performing the following steps:

1. Open a console and enter this
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

2. Add the following line to the end of the file
```
options snd-hda-intel model=toshiba
```

3. Reboot.

If someone else experiences the same problem, this would -hopefully- works for you too ):P

---

### Post by oldario on 2009-08-23
I had the same problem with my tecra s10 11w, ubuntu 9.04. Now it works perfectly, thanks !

---

### Post by jorgearevalo on 2009-09-04
Hello,

I had the same problem, and this was exactly the solution. Many thanks!

---

### Post by controlador on 2009-09-05
Thanks a lot,

  I have been searching the way to solve this problem the last months and now the sound is perfect.

Controlador

---

### Post by joseluissc on 2009-09-14
worked well on my toshiba s10-100 too, but I fell sound levels too lower even if I get it to the maximum on the mixer

---

### Post by web1star on 2010-04-16
> **tamerucar said:**
> Hi, my problem is solved by performing the following steps:

1. Open a console and enter this
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```2. Add the following line to the end of the file
```
options snd-hda-intel model=toshiba
```3. Reboot.

If someone else experiences the same problem, this would -hopefully- works for you too ):P
Hi I managed to solve this issue:
CODE:sudo gedit /etc/modprobe.d/alsa-base.conf
then add at the end of the file: 
options snd-hda-intel model=auto
reboot
And your Toshiba NB200 or NB205 /USA/ has perfect sound from your internal speakers:
Enjoy

---

