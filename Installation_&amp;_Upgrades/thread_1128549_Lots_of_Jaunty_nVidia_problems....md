---
title: "Lots of Jaunty nVidia problems..."
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Tahakki on 2009-04-17
Upgraded to Jaunty from Hardy earlier today.

The first thing I notice is that the much-hyped 'fast booting' isn't THERE. At ALL. It boots at the same speed as Hardy.

Then it gets bad. I've had to disable all proprietary drivers because they were causing such problems. Everything looks blurry on 1280, the resolution the login screen is at, and my monitor's native resolution. This still happens without the propitiatory drivers.

Everything worked fine in Hardy. Why can't I have the same driver in Jaunty? Why won't it boot faster? Why is it blurry?

Any help is massively appreciated, because I'm ready to switch back to Windoze. Help me out!

Some info:
Graphics: Geforce Ti 4400
Kernel: Latest one with Jaunty.
Driver I tried: 96
RAM: 512MB

I had these same stupid problems with Intrepid.

Thanks.

---

### Post by Therion on 2009-04-17
What method did you use to install the restricted driver for your system?  

I ask because you refer to it as "96" which, while I know you're referring to, would seem to indicate you're NOT using Ubuntu's restricted driver manager.

---

### Post by Tahakki on 2009-04-18
Actually, I used the Restricted Driver Manager under System -> Administration. In Intrepid, it popped up in the notification area, and I installed the only driver it offered me. I then upgraded to Jaunty and had to remove it as I couldn't boot on the newest kernel.

Jaunty calls it:
NVIDIA Accelerated Graphics Driver (Version 96) [Recommended]

Thanks.

---

### Post by sandy8925 on 2009-04-18
Your Geforce card is a bit old. I think 96 is the latest driver for the Geforce 4 series. About the problems.... try this page:

[ftp://download.nvidia.com/XFree86/Linux-x86/185.19/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/185.19/README/index.html)

You can find out how to configure your xorg.conf from there.

---

### Post by Tahakki on 2009-04-18
I tried re-installing the 96 driver, and somehow, it is now working. I'm not sure what I did to make it work. However, the problem with the blurry login screen still occurs. I'll try and fiddle with the X setting.

By the way, does RAM affect startup speed? I'm getting about 30 seconds atm.

---

### Post by Tahakki on 2009-04-18
I've fiddled around as much as I dared, and haven't yet found a solution for my blurry login screen.

What am I missing?

---

### Post by Neobuntu on 2009-09-17
Probably the refresh rate, which I set with...> sudo nvidia-settings Sudo, so I could save the change, in nvidia-settings. The nvidia-settings in the menu system did not have sudo before it.

---

