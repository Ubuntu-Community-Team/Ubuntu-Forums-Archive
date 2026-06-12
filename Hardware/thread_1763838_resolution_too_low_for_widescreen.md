---
title: "resolution too low for widescreen"
date: 2011-05-20
forum: Hardware
---

### Post by lroding on 2011-05-20
Hello,
I have an advent 7018 laptop ( 2gHz pentium 4-m, 1GB Ram , 60gb hard drive, Geforce 4 440Go graphics with a screen resolution of 1280x854) which previously I've used windows XP on. I have recently installed Xbuntu 11.04 on as a dual boot with XP.
On loading Xbuntu I find that the only resolutions i have available are up to a maximum 1024x768 which only occupies two thirds of my screen. I have read all the postings about changing xorg.conf but unfortunately this does not exist. I orginally installed the nvidia experimental 3d support drivers but when this didn't work i installed the nvidia accelerated graphics driver (version current) but this also doesn't work. If I go to the nvidia X server settings it tells me it isn't operating and to edit my X configeration file ............. which I don't appear to have. I have tried Dream Linux and Puppy linux on this laptop and they all work fine but as I use Ubuntu on both my other computers I would also like it on here too if possible.
Everthing else seems fine and runs really well
Can anyone help

---

### Post by Immolatus on 2011-05-21
You can generate your own xorg.conf. the best places to learn about this are the xorg wiki and the Arch Linux xorg wiki. I say Arch because you have to write or modify most things for your self when installing Arch so the documentation is really good. This is one of those pretty strange resolutions that would almost never be available to chose by default anyhow. You need to add it manually to the "screen" section. Just make sure you add in a fall back mode just in case(so you don't end up with no GUI).
You can add resolutions like:

"800x600" "1024x768" "1280x768" "1280x800"

xorg will fall back on the highest  "working" resolution.

---

