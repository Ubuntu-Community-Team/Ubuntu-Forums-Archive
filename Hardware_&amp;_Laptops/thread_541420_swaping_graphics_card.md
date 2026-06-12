---
title: "swaping graphics card"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by ramzaomega on 2007-09-02
is there is a way to use my nvidia fx 5200 instead of my on board graphics in ubuntu thanks 

ps i cant disable it on my bios and there is no jumpers to disable the onboard graphics thanks

---

### Post by taurus on 2007-09-02
Just use the right BusID for your nvidia graphic card in /etc/X11/xorg.conf.  If you are not sure which BusID it is, look at 

```
lspci | grep VGA
```

And to edit /etc/X11/xorg.conf, run

from window:
```
gksudo gedit /etc/X11/xorg.conf
```

from a console:
```
sudo nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by lckychrms on 2007-09-02
Yes, I have that card on one of my machines. The key is to install the NVIDIA drivers here is the URL for how to do so:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04)

---

### Post by ramzaomega on 2007-09-03
then what to change on it

---

### Post by lckychrms on 2007-09-03
You shouldn't have to change anything. Once you install the driver, the card will be recognized and the nvidia control center will be installed and you can tweak the card settings there

---

