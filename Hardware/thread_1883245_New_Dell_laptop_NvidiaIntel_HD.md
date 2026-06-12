---
title: "New Dell laptop Nvidia/Intel HD"
date: 2011-11-18
forum: Hardware
---

### Post by T08E on 2011-11-18
Hey, my old laptop recently died, so I've just got a new one from Dell. The system is supposed to have a 1 GB nVidia GeForce GT 525M graphics card. In the system information of the nVidia control panel it says that I have this card, but in dxdiag, it says my display is Intel HD.

Is this right, does my computer have both graphics cards, or have I just got the drivers from the nvidia card and not the card itself?

Hope that you can help with this because obviously if they have given me the wrong card I will need to get this sorted with Dell.

---

### Post by papibe on 2011-11-18
Could you post the result of this command?
```
lspci | grep -i vga
```
Regards.

---

### Post by seenthelite on 2011-11-18
What you have is nvidia optimus installed which requires a lot of configuration in linux.  Dell do not make it obvious in their advertising and most people assume the nvidia card is the only one installed. 
Some information on the situation with linux 

[http://en.wikipedia.org/wiki/Nvidia_Optimus](http://en.wikipedia.org/wiki/Nvidia_Optimus)
[http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg](http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg)

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

[http://ubuntuforums.org/showthread.php?t=1757821&page=5&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1757821&page=5&highlight=optimus)

---

### Post by T08E on 2011-11-19
Ah ok, thanks very much. It's good to know its there at least! I've yet to put ubuntu on, so can't give you the output from the command prompt papibe. I'm going to partition the hard drive and have ubuntu and windows. Thanks for your help guys.

---

