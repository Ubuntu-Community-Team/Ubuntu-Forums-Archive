---
title: "Need help installing nvidia drivers for optimus laptop on ubuntu 17.10"
date: 2017-11-01
forum: Hardware
---

### Post by mirul1996 on 2017-11-01
Hello, I need help on my XPS 15 (9550) to install the bumblebee and the nvidia drivers for it's GPU (GTX 960M). I have added the graphics ppa ([https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)) and use this guide to install it ([https://lenovolinux.blogspot.com.au/2016/05/bumblebee-on-lenovo-t440p-nvidia-gt.html](https://lenovolinux.blogspot.com.au/2016/05/bumblebee-on-lenovo-t440p-nvidia-gt.html)). I have also applied a workaround ```
[COLOR=#111111][FONT=Consolas]sudo ln -s /usr/lib/nvidia-384/bin/nvidia-persistenced /usr/bin/nvidia-persistenced[/FONT][/COLOR]
``` as indicated by this bug report ([https://bugs.launchpad.net/ubuntu/+source/nvidia-persistenced/+bug/1693123](https://bugs.launchpad.net/ubuntu/+source/nvidia-persistenced/+bug/1693123)) as earlier I have problems with the nvidia-persistenced during booting. However after installation and reboot, the display manager was not started and it gave a black screen with the booting messages as shown in this picture ([ATTACH=CONFIG]277368[/ATTACH]). 

I was able to recover back my system by booting to recovery and purge all nvidia drivers. After that the laptop was able to boot to the display manager. 

Here is the journald log should it help:[https://pastebin.com/HnKXPQxi](https://pastebin.com/HnKXPQxi)

---

