---
title: "Frames ATI vs Gnome3"
date: 2013-03-05
forum: Hardware
---

### Post by Godgothic182 on 2013-03-05
Hello,

 Recently I have installed ubuntu 12.04 64bits leaving behind the 32bits OSS. 
I have a "wonderful" ATI RADEON 1300x / 1550 x series and in my last  ubuntu I reached to a solution in order to get 1152 Frames with  glxgears....
It consisted in:
_______________________________
gksudo gedit /etc/default/grub 
  
then between the "" 
  
add radeon.modeset=0 
  
sudo update-grub 
________________________________

Now in Ubuntu 12.04 64 bits I get 300 frames despite the fact that the system works well, even with the effects of gnome3
However if I do this in order to have more frames....gnome starts only in classic mode without any effects.... 
so is there any way to solve this?

thanks for your attention

---

### Post by pme 72 on 2013-03-05
General concensus seems to be that glxgears is not an accurate benchmark of your systems performance. If everything works well, no issues, I would count myself amoung the lucky and be eternally grateful.

---

