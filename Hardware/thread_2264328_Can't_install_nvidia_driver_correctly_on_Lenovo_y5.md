---
title: "Can't install nvidia driver correctly on Lenovo y50-70"
date: 2015-02-06
forum: Hardware
---

### Post by nigro.orlando on 2015-02-06
Hi,
I have recently installed Kubuntu 14.04 on my lenovo y50 and I'm trying to install the nvidia drivers but when I do it I always get a black screen after booting. The only one that doesn't have this problem is the 331 but still is not working since when I go to the nvidia-setting it won't make me change from intel to nvidia but it gives me an error message which is not actually a message but just a big X.

I don't know what's the problem because I already tested to install nvidia on a Lenovo y50 and that time it worked nicely but now that I'm doing it again it doens't work. The other lenovo had the same card, but less ram and this new lenovo har a UHD screen, can all this matter?

There probably are similar topic on the forum but I couldn't manage to apply that on my case. 
I hope someone can help me!

---

### Post by gregor-skrt on 2015-02-16
Yeah, same problem here. Now I'm doing clean install, edgers ppa, nvidia-346 driver. I tried 340 but after reboot I can't see lightdm only black screen. It works when switching to intel with prime....

---

### Post by gregor-skrt on 2015-02-16
Final solution : I don't use edgers drivers - don't know why they don't work - I installed drivers from  This PPA: [COLOR=#000000][FONT=Ubuntu Mono]ppa:mamarley/nvidia, I still couldn't switch between graphic cards - I had to use: [/FONT][/COLOR]sudo update-alternatives --config x86_64-linux-gnu_gl_conf to choose propper driver.

---

