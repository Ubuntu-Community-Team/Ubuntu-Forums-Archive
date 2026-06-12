---
title: "just installed ubuntu 9.04 now what?"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by cowboyup6983 on 2009-10-19
i want to play my mp3s mkv files, and dvd iso image files. 

also how do i get the drivers for my old nvidia card, i got 8800GTS. should i install something or just go to 
system>
admin>
hardware drivers. 

it says "no proprietary drivers are in use on the system"

NVIDIA accelerated graphics drivers (version 180 recommended)
NVIDIA accelerated graphics drivers (version 173)


should i install my drivers this way, i want to soon start playing with compiz fusion to get all the eye candy on linx. please help

---

### Post by Jose Catre-Vandis on 2009-10-19
Yes, install the 180 drivers.

for restricted formats install the extras:
```
sudo apt-get install ubuntu-restricted-extras
```
or search for this in synaptic

---

### Post by cowboyup6983 on 2009-10-19
> **Jose Catre-Vandis said:**
> Yes, install the 180 drivers.

for restricted formats install the extras:
```
sudo apt-get install ubuntu-restricted-extras
```
or search for this in synaptic


what do u mean for restricted formats??? install the extras? what does those to things mean

do u mean for me to play my music and movie files, i think so. i will do just that. what player does everyone recommend. i like vlc player but i think it might be hard to install.

---

### Post by stlsaint on 2009-10-19
for media ie encrypted dvds and music you need to enable/install [medibuntu]("https://help.ubuntu.com/community/Medibuntu"). 

also yes you need to enable the recommended driver to enable normal desktop graphics to enable compiz.

Welcome to Ubuntu:)

---

### Post by cwbar_1 on 2009-10-19
Follow this guide.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Jose Catre-Vandis on 2009-10-21
> **stlsaint said:**
> for media ie encrypted dvds and music you need to enable/install [medibuntu]("https://help.ubuntu.com/community/Medibuntu"). 


Do you really need medibuntu packages ?

I haven't used anything from medibuntu on my Jaunty installation, just packages from the repos, and I seem to be able to play any media I throw at it, including encrypted DVDs?

---

### Post by themusicalduck on 2009-10-21
vlc is really easy to install. Just use

```
sudo apt-get install vlc
```

Or search for it under Add/Remove and install it there.

---

