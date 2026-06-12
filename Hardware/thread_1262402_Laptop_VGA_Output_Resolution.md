---
title: "Laptop VGA Output Resolution"
date: 2009-09-09
forum: Hardware
---

### Post by c00lryguy on 2009-09-09
Hello all, I just reinstalled Ubuntu with 9.04 on my (crappy) laptop coming from 8.04. I have the laptop connected with a VGA output on the laptop to my flat screen monitor, which turns off the laptop screen.

Everything runs great, it's just the maximum resolution only goes up to 800x600. On 8.04 I was able to set it to 1024×768 (which is still too big for me, but it was better than 800x600). 

I ran xrandr and this is the output it gives me:
```
ryguy@ryguy-laptop:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
```Is there anyway I can set it to 1024x768, or even better would be 1280x1024? I know the monitor is capable of such resolutions.

---

### Post by ytene on 2009-09-10
Hi,

I'm looking to solve a similar problem and in my research I came across the following page on the wiki:-

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

It describes how you can interrogate hardware to determine the available display options and then progress them from there.

I've just purchased a Dell 2408WFP 24" Monitor that can go to 1920x1200, but my machine [an Acer Revo R2600 with ubuntu 9.04] seems to max out at 1600x1200 and with the new X config it's not possible to just go in and manually hack xorg.conf as you could in "the good old days". Sheesh.

Good luck with your question...

---

