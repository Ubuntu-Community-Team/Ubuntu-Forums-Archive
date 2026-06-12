---
title: "slow boot time: 'integrated sync not supported'"
date: 2009-11-25
forum: Hardware
---

### Post by akhilbehl on 2009-11-25
hey.. i have been really disappointed with the boot times of karmic.. which are longer than those of jaunty that i upgraded from..

i looked at dmesg and this part of the output is really confusing:

[   25.301944] Bridge firewalling registered
[   27.409551] integrated sync not supported
[   27.454937] [drm] TV-14: set mode NTSC 480i 0
[   27.595699] [drm] TV-14: set mode NTSC 480i 0
[   27.834322] integrated sync not supported
[   27.904646] [drm] TV-14: set mode NTSC 480i 0
[   28.045343] [drm] TV-14: set mode NTSC 480i 0
[   28.108035] eth1: no IPv6 routers present
[   37.677074] integrated sync not supported
[   37.718754] [drm] TV-14: set mode NTSC 480i 0
[   37.860335] [drm] TV-14: set mode NTSC 480i 0
[   38.123144] integrated sync not supported
[   38.164886] [drm] TV-14: set mode NTSC 480i 0
[   38.306015] [drm] TV-14: set mode NTSC 480i 0
[   38.534409] integrated sync not supported
[   38.576076] [drm] TV-14: set mode NTSC 480i 0
[   38.716380] [drm] TV-14: set mode NTSC 480i 0
[   40.762108] integrated sync not supported
[   40.803772] [drm] TV-14: set mode NTSC 480i 0
[   40.945383] [drm] TV-14: set mode NTSC 480i 0
[  261.777123] CE: hpet increasing min_delta_ns to 15000 nsec

I am losing 15 secs in the boot time (and what is the last thing?)

i can not understand the error at all.. i tried googling and it did not find me anything either.. so i am writing here wishing some one would at the least explain what this means.. and if possible.. help me to reduce the boot time by removing this problem.

thanks in anticipation!

---

### Post by LnRSoft on 2009-12-16
I'm facing the same problem ... any advice?
vga intel 945

---

