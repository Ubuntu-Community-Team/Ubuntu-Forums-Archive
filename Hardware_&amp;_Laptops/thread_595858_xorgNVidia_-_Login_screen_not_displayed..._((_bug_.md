---
title: "xorg/NVidia - Login screen not displayed... (( bug? ))"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by Knoeki on 2007-10-29
Hi there... not sure if this is the right place to post, but since I'm using a laptop...

I noticed a strange bug. When I install Ubuntu, it works fine, reboots, I get the login screen, no problem.
I install updates and the restricted drivers. after this, I have to reboot again.

here's where the problems occur:

when I boot normally, I get the loading screen, but after that, I just hear the drum sound, and the display turns off (( even backlight goes off )). When I try to switch to a VT, they all just have a blinking cursor, nothing else.

Right, so I figured out a way to get in... when booting, select 'Recover Mode' (( or however it's called, can't remember right now )), wait for it to start up.
When booted, you are logged in as root. log out, and X will start, after which you switch to a VT, which suddenly *do* work for some reason. then do the following:
```
sudo rm -f /tmp/.X0-lock
```
and then start X again. THEN I'm logged in.

Funny thing is, it's only the login screen that appears to be broken... everything else works, and I'd gladly get it to work again, or simply just disable xorg from automatically starting.

My config (( the related stuff )):

NVidia GeForce 4

Ubuntu 7.10


(( note: it worked fine with Kubuntu 7.04, I just don't like KDE all that much ^^ ))


if you need more info, please tell me what! I really hope to solve this somehow, because logging in now is a bit... well, uncomfortable. I can do it somewhat quickly, but still... .. .

---

