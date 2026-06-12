---
title: "Problem getting 8.04 LTS video resolution set correctly."
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by jowensnh on 2009-06-25
I have an old desktop PC that I was rebuilding for my son to use. It was running 8.04, but when I upgraded to 8.10 there was an incompatibility with the video card I have and the newer kernel and I was not able to get it to run anything higher than 800x600 resolution. I tried to install 9.04 with the same results. Now I would like to go back to 8.04 so I downloaded it again and burned it to a CD. For some reason I still cannot get it to go any higher than 800x600. If I install the nvidia drivers for the card I can only get 640x480. The machine is a Dell PIII with an Nvidia Quadro 4 nvs agp card. I am using a lcd monitor that runs at 1024x768 60 hz. Any ideas on how I can get this to work with 8.04? I looked in the xorg.conf file, but it does not have any settings in it.

Thanks,

Jerry

---

### Post by mikewhatever on 2009-06-26
8.04 has a tool called displayconfig-gtk hiding in the menu. If you don't want to dig for it, use **sudo displayconfig-gtk** command.

---

