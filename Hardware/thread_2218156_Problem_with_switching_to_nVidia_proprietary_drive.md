---
title: "Problem with switching to nVidia proprietary drivers (14.04 Ubuntu, full release)"
date: 2014-04-19
forum: Hardware
---

### Post by Sean_Ooley on 2014-04-19
When I enable proprietary drivers from settings or install them using  ppa:ubuntu-x-swat/x-updates drivers, it works almost perfectly, except that the boot screen isn't a nice graphical screen, it is a text based screen. This is not terrible, but it is annoying. Is there anything I can do to fix this from happening?

---

### Post by SeijiSensei on 2014-04-19
I've found that to be true for nearly every release with the NVIDIA proprietary drivers.  I don't know why, but I gave up thinking about it since I rarely boot my computers more than a couple of times per week at most.

My bigger problem with NVIDIA drivers is that the text can sometimes be miniscule.  In that case you need to generate an xorg.conf file and add the [DPI]("http://www.mythtv.org/wiki/Specifying_DPI_for_NVIDIA_Cards") option.

---

### Post by mrlamud2 on 2014-04-20
Try this [http://www.namanb.com/2010/05/changing-bootup-resolution-plymouth-in-ubuntu-10-04-lucid-lynx.html](http://www.namanb.com/2010/05/changing-bootup-resolution-plymouth-in-ubuntu-10-04-lucid-lynx.html)
Credit :: [www.namanb.com](www.namanb.com)

I switched from Windows to Ubuntu 12.04 several years ago and found the same problem. 
The above link works for me.

 However , I recommend you to run vbeinfo in Grub command to see your graphic card resolutions before go on with the above mentioned method.

---

