---
title: "[help]8.04 display problem (not full screen) on Toshiba Portege R500"
date: 2008-12-30
forum: Hardware
---

### Post by pigling on 2008-12-30
Hi all,
I installed 6.06(Dapper Drake) on my Toshiba Portege R500 by netboot since my R500 has no CD rom, which was bought in 2003. Everything works well, i.e., WiFi, audio, display... except the machine cannot reboot well when I clicked the reboot button. Then I installed 8.04(Hardy Heron) and there is a display problem. It does not display full screen but a smaller size on the screen. The view is in the center of the screen, and the gap is black for the four sides. However, other things work well, i.e., WiFi, audio, and reboot problem solved. I google for this issue but find no answer. I wish you may help. Thanks.
P.S. May this problem disappear in 8.10 (Intrepid)? Should I change to the latest release?

Thanks.

regards,
qichao

---

### Post by teaker1s on 2008-12-30
We used to be able to
```
dpkg-reconfigure xserver-xorg
``` which has since depreciated in later versions, but should work in dapper and bring up gui

later versions
It's xserver setup in xorg.conf thay you will need to find settings for your model, you may find **xrandr** helpful
[http://www.cyberciti.biz/tips/linux-resize-screen-size-quickly.html]("http://www.cyberciti.biz/tips/linux-resize-screen-size-quickly.html")

---

