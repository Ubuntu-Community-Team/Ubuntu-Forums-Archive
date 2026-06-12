---
title: "Nvidia gtx 980 flashing tty black screen"
date: 2015-02-11
forum: Hardware
---

### Post by gigurra on 2015-02-11
I've been using ubuntu on my laptop for a while and it works great, so I decided to install it on my desktop PC as well.

I installed 14.04 64 bit but immediately ran into the problem of getting black screen if I pressed CTRL+ALT+1.. - This was before I installed any nvidia drivers.
Modifying the /etc/default/grub solved it

But after installing nvidia 346.35 drivers the problem came back - worse, not only does the screen go black if I press CTL alt 1, it also starts flashing wildly (I recorded a video of it here [https://www.youtube.com/watch?v=pS73Lf4s8Pk](https://www.youtube.com/watch?v=pS73Lf4s8Pk)).

You can see the values Ive experimented in the /etc/default/grub to try to solve this, but they dont seem to have any effect at all. 
The grub menus work fine and the console is also fine UNTIL x and the nvidia drivers loads, when all *** breaks lose and the screen starts flashing.

Everything (except tty1-..) works fine as soon as I enter the x desktop (sry if I use the wrong terminology. I've just recently migrated my non-work environment from windows :))

Hardware is a gtx980, and monitor an asus rog swift monitor (2560x1440 @ 144 Hz).
Another problem I have is that I cannot seem to permanently set my refresh rate to 144 Hz (ubuntu ignores xorg.conf on boot?)  - but perhaps that's better left for another thread...
xrandr --output DP-4 --mode 2560x1440 --rate 144 does the trick for the refresh rate, but, not sure how to make that permanent :P - Heck Id be happy if I could just put it in some auto script (tried .profile and .xinitrc without any luck )

---

