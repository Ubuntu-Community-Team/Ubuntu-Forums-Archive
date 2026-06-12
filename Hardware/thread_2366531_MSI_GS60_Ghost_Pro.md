---
title: "MSI GS60 Ghost Pro"
date: 2017-07-18
forum: Hardware
---

### Post by itang96 on 2017-07-18
Hey guys,

I'm a relatively new user to Ubuntu. I got my MSI laptop to dual boot windows and ubuntu around two months ago. Recently, I've started to notice that the battery life on my laptop is very short when I boot into Ubuntu and I've been looking at various forums for a fix but still haven't found one that helps yet.

I appreciate any kind of help/tips. Please let me know if I should provide anymore information (this is my first time posting in a forum about anything tech related) 

Thanks in advance!

---

### Post by efflandt on 2017-07-19
I have not looked up that specific model, but if you are using Nvidia graphics all of the time (instead of just when gaming), that could be it. You can change which graphics are being used from **NVIDIA X Server Settings**. You may either need to log out of X and back in switching Nvidia to Intel, or possibly reboot if switching Intel to Nvidia (I was not using nomodeset). The power LED of my GE60-2OE would be **[COLOR=#0000ff]blue[/COLOR]** when using low power Intel graphics and **[COLOR=#ff8c00]amber[/COLOR]** when using higher power Nvidia graphics, but unfortunately that laptop no longer turns on properly (just cycles on 7 sec as power & fans wind down, off 4 sec, on 7 sec, etc. until holding power button to keep it off).

---

### Post by itang96 on 2017-07-27
Thanks! I'll check this out

---

