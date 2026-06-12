---
title: "Acer Extensa 4620Z headphone jack not working"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by ahfu on 2007-12-23
Hi all,

I have just installed my first ever Linux on my new laptop - Acer Extensa 4620Z..
Most of the things worked fine except that my headphone jack..
My laptop internal speaker works fine but when i plug in a headphone, there is no sound from the headphone but the sound still continued to be from the internal speaker..

I did follow the instructions at the notes section at [https://wiki.ubuntu.com/LaptopTestingTeam/AcerExtensa5220](https://wiki.ubuntu.com/LaptopTestingTeam/AcerExtensa5220) but it did not work.. maybe because mine is Acer Extensa 4620Z

I am running Ubuntu v7.10

As I am a newbie to linux, i would appreciate if replies are kept at a level easy to understand for a newbie.. Thanks!

Ah Fu

---

### Post by silverstormboy on 2008-01-22
Hi,

I also use 4620Z.

I install Ubuntu 7.10 dual boot with vista and manage to get the headphone jack working.

to get headphone jack working, follow this link:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

install linux-backports-modules-generic ( using synaptic)

add options line below to first line of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

restart.

but i didnt manage to get acer webcam working on amsn and internal mic also not working.
if you manage to make it work, please  share it with me, Thanks.

---

### Post by sean42 on 2008-02-23
I have this laptop and silverstormboy's fix worked for my machine

---

