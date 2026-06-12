---
title: "Radeon 9200 se"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by benoit.borlee on 2005-04-08
Hi,

I've just tried the 5.04 liveCD for AMD 64. But after the startup, the screen appears completely scrambled. Only the mouse pointer seems OK. I can hear the intro music but I'm not able to see any icons or menus.

Could it be that my graphic card is not supported ? It's a radeon 9200 SE. 

Could it be solved if I try the install CD instead ?

Thanks

Benoit

---

### Post by lilian on 2005-06-29
Hi,

I had the same problem. I solved this by rebooting in recovery mode, edited the /etc/X11/xorg.conf and setting "15" as the default depth for my graphic card.

Regards
Lilian

---

### Post by lucaflea on 2005-07-07
i have the same problem....
but, i'm a newnewnewby, where do i have to write "/etc/X11/xorg.conf " ??

when i boot with recovery mode i come to this:

root@ubuntu:~#

and than....


luca

---

### Post by Siorfin on 2005-07-07
at the prompt you listed type pico /etc/X11/xorg.conf (case sensitive) then use the arrow keys to scroll down to the desired line and edit it. Use I believe ctrl-x to exit then hit y to save changes and enter. Reboot.

---

