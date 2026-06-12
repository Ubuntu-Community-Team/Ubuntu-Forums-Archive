---
title: "ATi Radeon Xpress 200M 5955 and colorful lines"
date: 2008-07-20
forum: Hardware
---

### Post by KDB9000 on 2008-07-20
I have an HP DV5000 Laptop that has the Radeon Xpress 200M in it. I have the latest drivers from the ATi website and installed them. They work well for just about everything, except when I press Crtl + Alt + F1 thu F6. All I get are vertical colorful lines. They are always different and sometimes they are flashing a couple of them. I also see then when I shut the laptop down. Anyone know how to fix this?

---

### Post by nqnutn on 2008-08-08
I also have a HP DV5000

i had tons of video problems with the proprietary driver, i tried just about everything

actually i messed so much with my xorg.conf that i wasn't able to use the driver correctly anymore so i removed it >System>Administration>Hardware --> uncheck ATI accelerated driver

 
NOW everything works just perfect!

no colorful lines

no video studder


cons:

cant use the added visual desktop effects

games like "glest" still crash


overall the best solution i found so far

---

### Post by sidrit on 2008-08-10
Well, i have the same card. disabling the drivers sorts out most of problems , but you won't be able to have the desktop effects.
For that you need fglrx drivers and the At driver enabled.

here's a howto

[http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/]("http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/")

hope it helps.
sid

---

### Post by KDB9000 on 2008-09-22
Sorry for the late response. No it didn't help. Thx for trying. Anyone else have a problem like this?

---

### Post by pir4 on 2008-10-02
In /etc/modprobe.d/blacklist-framebuffer uncomment vesafb and that will do it.

---

