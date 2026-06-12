---
title: "How do I get the nforce410 chipset working?"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by HIGHLIFE on 2006-03-01
Could someone plz help me get this chipset working? 
No ethernet
No sound
xserver doesnt work unless reconfigured

I tried installing the Nvidea drivers from here:
[http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html")

but I got an error with something about not having gcc3.4 even after I installed it why is this? 

thx in advance

---

### Post by el3ktro on 2006-03-01
You have to tell the installer to actually use gcc-3.4, because gcc-4.0 is set as the default. Do this:

apt-get build-essentials, then downlad the nvidia installer for the network & audio card, then log in as root and type

export CC=gcc-3.4

log off as root, then type the same as normal user and then start the installer with

sudo ./nforce....run

This worked fine for me and should do fine for your too :-) You can also search the forums for how to intall the latest nvidia drivers by hand, that's where I found these instructions!


Tom

---

### Post by HIGHLIFE on 2006-03-02
Ok I got ethernet working but I can't get the onboard sound up.:( 
I also have a sound blaster X-fi sound card (I know there is no hope of getting this card working right now so thats why im trying to get my onboard up) would this be screwing it up and if so how could i fix it?

---

### Post by HIGHLIFE on 2006-03-03
bump

---

