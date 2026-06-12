---
title: "Xorg startup problem"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by pontius_pilatus on 2006-01-02
hi, I'm a new ubuntu user, but not new to linux/unix environment

so my Milion $ question is:
has anyone installed ubuntu on a Intel SE7525 RP2 and Nv Quadro 1400 PCI
or atleast with intel chips SE75xx and quadro PCI-x

and my million $ problem is:
can't start X window, no screens found, nv is on PCI:3.0.0

have tried almost all tips in these forum, except kernel recompile :confused: 
I think it's something to do with quadro+PCI+chipset+bios config, maybe

very greatfull if somebody here can help me

BTW: Great forum, i've been to alot of linux forum like redhat, slackware and mandrake err mandriva ;) , ubuntu is linux at 5 years old yet thinks like 40 years old :p

---

### Post by Jammy_Stuff on 2006-01-02
Try booting into the recovery console and typing:

```
sudo dpkg-reconfigure xserver-xorg
```

then work out the right driver for your device.

---

### Post by pontius_pilatus on 2006-01-02
thanks for the reply...
yes I've tried that, I use nv as driver, so as to just enter X with default first

I forgot to mention that intel se7525 has a onboard vga ATI, which I disable in bios

ok x.org log said that it can't find the frame buffer device nv(0)

thanks
Pontius

---

