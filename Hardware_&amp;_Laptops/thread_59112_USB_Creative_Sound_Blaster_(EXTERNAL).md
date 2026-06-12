---
title: "USB Creative Sound Blaster (EXTERNAL)"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by brianmuse on 2005-08-22
I know that there have been many posts about sound problems in Ubuntu, but I haven't been able to find any information on external sound cards. 

```

 AUDIGY 2 USERS:
Install the linux-headers package that suits your kernel. I am running kernel 2.6.10-5-386

sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10

cd /usr/src
sudo wget ftp://ftp.alsa-project.org/pub/driv...r-1.0.8.tar.bz2
tar xvjf alsa-driver-1.0.8.tar.bz2
cd alsa-driver-1.0.8
sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
sudo make
sudo make install

sudo nano /etc/modules
add in

snd-pcm-oss
snd-emu10k1
snd-mixer-oss

```


I followed all of the above steps in the sticky thread "Hoary Sound Broke?," except I substituted 

```
emu10k1
```

with 

```
usb-audio
```

This, however, still does not work. I am completely new to linux.

The funny thing is that in XMMS, I can set the drivers and the device to the sound card and it works fine (well...it works for the two front speakers and not the complete 5.1), however no matter what I do, I cant get anything else to use anything but my latop speakers.

Please help!

Thanks in advance!

EDIT: it should also be noted that I updated alsa to the latest version wwhich adds "usb-audio"

---

### Post by brianmuse on 2005-08-23
bump?

---

### Post by brianmuse on 2005-08-24
Is there no one that can help me!?

---

### Post by Tschaeck on 2005-09-20
[QUOTE=brianmuse]I know that there have been many posts about sound problems in Ubuntu, but I haven't been able to find any information on external sound cards. 

```

 AUDIGY 2 USERS:
Install the linux-headers package that suits your kernel. I am running kernel 2.6.10-5-386

sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10

cd /usr/src
sudo wget ftp://ftp.alsa-project.org/pub/driv...r-1.0.8.tar.bz2
tar xvjf alsa-driver-1.0.8.tar.bz2
cd alsa-driver-1.0.8
sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
sudo make
sudo make install

sudo nano /etc/modules
add in

snd-pcm-oss
snd-emu10k1
snd-mixer-oss

```


I followed all of the above steps in the sticky thread "Hoary Sound Broke?," except I substituted 

```
emu10k1
```

with 

```
usb-audio
```

This, however, still does not work. I am completely new to linux.

The funny thing is that in XMMS, I can set the drivers and the device to the sound card and it works fine (well...it works for the two front speakers and not the complete 5.1), however no matter what I do, I cant get anything else to use anything but my latop speakers.

Please help!

Thanks in advance!

EDIT: it should also be noted that I updated alsa to the latest version wwhich adds "usb-audio"[/QUOTE]


only your front speakers work? have you already played around with alsa-mixer? maybe the rear speackers are muted by default and you just have to turn the sliders up.

---

