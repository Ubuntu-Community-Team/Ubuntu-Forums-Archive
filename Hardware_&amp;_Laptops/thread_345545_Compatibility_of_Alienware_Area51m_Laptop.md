---
title: "Compatibility of Alienware Area51m Laptop"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by erugalatha on 2007-01-24
Hi,

I'm thinking of installing ubuntu on my alienware laptop but I've tried another installation of Linux on it before and basically it made a nice silver brick out of my alienware. :( 

Does anyone know if all hardware works after installing?  Any bad experiences between Alienware and Ubuntu?  Does the soft/win modem work when ubuntu is installed?

Thanks for your comments.

---

### Post by loserboy on 2007-01-24
just run the livecd and see how it does 1st

---

### Post by sengoku on 2007-05-01
well, i have run ubuntu on my area 51m for the last few versions. it mostly works fine :)

some things to watch - enabling nvidia's driver gives some horrible screen corruption - the fix is to go to /etc/X11/xorg.conf and in the graphics "Device" section add :

Option "ModeValidation" "NoVertRefreshCheck"

the only other issue i have is that my echo indigo io card isn't recognised by default, but installing the latest alsa-firmware (you don't need the others) from alsa-project.org fixes that.

otherwise, enjoy. :)

---

