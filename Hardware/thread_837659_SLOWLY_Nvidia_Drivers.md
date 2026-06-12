---
title: "SLOWLY Nvidia Drivers?"
date: 2008-06-22
forum: Hardware
---

### Post by nl2br on 2008-06-22
Hello, I have a MSI NX8500GT video card and i feel it really SLOWLY while, for example, switching between tabs in Firefox. (i mean, 0.5 sec delay, when there is a mid-lot of graphics in both webpages).

I don't understand why, when i had an old GeForce 6200 that didn't happen to me.

Anyone know this situation? I am trying with the last drivers from EnvyNG.

Thanks, nl2br.

---

### Post by StyphaX on 2008-06-27
Ola!

I have the same problem with the official Nvidia driver (8800GT). Switching between tabs take about 0.5s econds but there's other problem.

In fact, firefox is also slow when a page use javascript and when i scroll on a long page... (like facebook)

I think that the integration of gecko into Ubuntu Hardy cause theses problems (in firefox 2-3 and epiphany) because with any other browser (like Opera or konkeror), i have no problems....

---

### Post by starcannon on 2008-06-27
could be the Powermizer in the Nvidia driver as well.

You could try enabling coolbits which will allow you to set the driver to run the hardware at performance level settings all the time, or even over clock if you so choose.

to do so you will need to edit your xorg configuration file:

```

gksudo gedit /etc/X11/xorg.conf

```

Then you will need to find this entry and modify it to look like mine:

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option	   "Coolbits"	"1"
EndSection

```

Now you can open nvidia settings and make changes to powermizer:

```
gksudo nvidia-settings
```

GL and have fun.

---

### Post by sdennie on 2008-06-27
There have been huge complaints about this on the nvidia forums: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14).  However, I'm using the 173.14.09 drivers with an 8400M GS and the performance is actually very good so, possibly just switching drivers would help.

---

### Post by starcannon on 2008-06-27
I'm using same drivers, and on this laptop same chipset as Vor, and like Vor my performance is fine.

When I was running compiz all the time I used coolbits to get rid of the slight lag when initiating an intense effect or desktop cube rotation.

---

### Post by StyphaX on 2008-06-29
I have no LAG when using compiz, just in firefox and i Have the 173.14.05 driver :)

Coolbit can't resolve my problem :(

---

