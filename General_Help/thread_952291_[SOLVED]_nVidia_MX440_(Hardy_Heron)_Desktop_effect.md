---
title: "[SOLVED] nVidia MX440 (Hardy Heron) Desktop effects"
date: 2008-10-19
forum: General Help
---

### Post by Tails5 on 2008-10-19
I have Ubuntu 8.04 Hardy Heron, and I installed the proprietary drivers that it required. But it locked me in 640x480, so I uninstalled it and installed the drivers from nVidia.com and now I have 1024x768, but I can't enable desktop effects because it says I have to enable proprietary drivers (the same ones that locked me at 640x480). Is there any way to convince Ubuntu that I DO have the drivers running, without using the ones it wants me to use?

EDIT: SOLVED: I ran Envy and then did 'gksudo displayconfig-gtk' and set my monitor to CRT 1024x768 and now EVERYTHING works. If anyone else is having this problem, you get envy from [http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

---

