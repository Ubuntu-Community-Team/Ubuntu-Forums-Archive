---
title: "Ubuntu doesn't start with Radeon HD 6470M"
date: 2011-06-13
forum: Hardware
---

### Post by iggi916 on 2011-06-13
I have installed Wubi on my HP pavilion dm4 and it works fine. However, I have the integrated Intel graphics card and a Radeon 6470M card. When I boot into Ubuntu, I just get a black screen after the grub prompt. I can avoid this by booting into Windows, switching to the integrated graphics card and booting into Ubuntu.

I was just wondering if there is a way to boot into Ubuntu with my Radeon card, or at least set it up to switch to Intel during boot?

Also, I think I might have removed the drivers for the Radeon card, but I'm not sure since I am a Linux newbie.

Thanks for any help!

---

### Post by iggi916 on 2011-06-15
OK, so I'm halfway there. I managed to get my ubuntu to boot by blacklisting the radeon module as in [this]("http://ubuntuforums.org/showthread.php?t=1744188") thread. 

However, the Radeon card is still on; I want to turn it off during bootup using vgaswitcheroo. When radeon is blacklisted, vgaswitcheroo does not exist, so I added the following line to my /etc/rc.local file:
```
modprobe radeon
```
That "turns on" the radeon controller (or something to that effect) and vgaswitcheroo is available in the /sys/kernel/debug folder. However, I always get "permission denied" for /sys/kernel/debug/vgaswitcheroo/switch, so I cannot use
```
echo OFF > /sys/kernel/debug/vgawitcheroo/switch
```
to turn off the discrete card. I can't even use sudo for it; it only works as root.

I tried putting in ```
chown root:plugdev /sys/kernel/debug/vgaswitcheroo/switch
``` in my rc.local file but I still cannot access vgaswitcheroo. I even tried ```
sudo -i
``` in there, but clearly that doesn't work.

Any ideas?

---

### Post by pitaj on 2011-06-24
Hey I guess this graphics card just isn't supported yet.  You'll either have to use the way you are or boot up in nomodeset permanently like me.  How do u manually switch to the intel card, by the way?

Also, you maybe can use su instead of sudo, i might not work though.

---

### Post by iggi916 on 2011-06-25
As far as I understand, if you boot up in modeset=no, the radeon card isn't 'on' so vgaswitcheroo isn't available. 

If it were, you would be able to switch to the integrated (Intel) card by "sudo echo INT > /sys/kernel/debug/vgaswitcheroo/switch" and then "sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" to turn off the nonfunctioning card (in this case the discrete card).

---

