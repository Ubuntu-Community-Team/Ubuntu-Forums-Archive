---
title: "[SOLVED] call the automatic hadware detection/installation from ubuntu installationhi"
date: 2008-07-12
forum: Hardware
---

### Post by el_Nacho on 2008-07-12
hi,

my problem is i changed my graphicscard driver with that "screens and graphics" tool.
it actually worked really well, its an intel on board one and since hardy i dont even have to use 915resolution anymore ...

now when gnome starts, i get an error message saying it cant operate in high resolution. changing the driver seems not to have any sort of effect. eversince i have this problem videos are slow, no visual effects, when i close the lid and open it again the screen remains black (it seems gnome then stopped working)

i tried the recovery mode from my alternative installation cd but there is no such option and it wants me to format my hdd :/

what i need is to start the autodetection from installation or a hint where i can find the config files which save that information.



thanks in advance, nacho

---

### Post by ProbablyX on 2008-07-12
> **el_Nacho said:**
> hi,

my problem is i changed my graphicscard driver with that "screens and graphics" tool.
it actually worked really well, its an intel on board one and since hardy i dont even have to use 915resolution anymore ...

now when gnome starts, i get an error message saying it cant operate in high resolution. changing the driver seems not to have any sort of effect. eversince i have this problem videos are slow, no visual effects, when i close the lid and open it again the screen remains black (it seems gnome then stopped working)

i tried the recovery mode from my alternative installation cd but there is no such option and it wants me to format my hdd :/

what i need is to start the autodetection from installation or a hint where i can find the config files which save that information.



thanks in advance, nacho

```

sudo cp /etc/X11/xorg.conf ~/xorg.backup
sudo dpkg-reconfigure xserver-xorg

```

Should make the xserver redetect your graphics card's driver. The first like also backs up your xorg.conf. If the reconfigure doesnt help you can restore the xorg.conf from your home dir and "xorg.backup"

---

### Post by el_Nacho on 2008-07-13
ok now it seems to be working, i just got 2 other problems now ...

1. my keyboard cannot type some special (german) characters eventhough i chose de:nodeadkeys as the type which woked well in the past, but i think i'll be able to figure thatone out myself

2. that "screens and graphics tool" recognizes my card (915 is correct) but tells me there is no driver. whats that? (screenshot attached)

just want to make sure its back at normal again ...

---

### Post by ProbablyX on 2008-07-13
> **el_Nacho said:**
> ok now it seems to be working, i just got 2 other problems now ...

1. my keyboard cannot type some special (german) characters eventhough i chose de:nodeadkeys as the type which woked well in the past, but i think i'll be able to figure thatone out myself


Go into text mode and enter:
```

sudo nano /etc/X11/xorg.conf

```

Locate a line starting with:
	Option		"XkbLayout"

Make it say
	Option		"XkbLayout"	"de"

Now reboot (or restart the xserver) for german keys

---

### Post by ProbablyX on 2008-07-13
> **el_Nacho said:**
> 
2. that "screens and graphics tool" recognizes my card (915 is correct) but tells me there is no driver. whats that? (screenshot attached)

Sorry forgot the second question.

If your PC works, I wouldn't pay too much attention to that. probably just a bug :)

---

### Post by phoenix_abhi on 2008-07-13
ur driver is PnP

---

### Post by el_Nacho on 2008-07-14
ok, thanks a lot for helping me!

---

