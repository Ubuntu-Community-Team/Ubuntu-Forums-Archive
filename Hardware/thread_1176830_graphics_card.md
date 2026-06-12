---
title: "graphics card"
date: 2009-06-02
forum: Hardware
---

### Post by UncleMonty on 2009-06-02
How can I reconfigure the graphics card in Jaunty?

---

### Post by b6of12 on 2009-06-02
helps if you give more info like chip brand (ATI Nvidia matrox etc )

I think you wont to do this 
well first back up
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup I think :D 

```
than this
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
this well reset your you your x

---

### Post by UncleMonty on 2009-06-02
> **b6of12 said:**
> helps if you give more info like chip brand (ATI Nvidia matrox etc )

I think you wont to do this 
well first back up
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup I think :D 

```
than this
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
this well reset your you your x

"]helps if you give more info like chip brand (ATI Nvidia matrox etc )"

I use Intel

---

### Post by UncleMonty on 2009-06-02
> **UncleMonty said:**
> "]helps if you give more info like chip brand (ATI Nvidia matrox etc )"

I think it's intel - how can I be sure?

Okay this is what happened:


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090603005915




Where do I go from here?

---

### Post by UncleMonty on 2009-06-02
> **UncleMonty said:**
> Okay this is what happened:


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090603005915




Where do I go from here?



Is intel not a good graphics card to use in Ubuntu?

---

### Post by b6of12 on 2009-06-03
what props are you having

what type of video card you have

if you Don't now do this 
```
lspci
```

woops forgot it auto backs up

---

### Post by b6of12 on 2009-06-05
are you having the same prop as this gie 

[http://ubuntuforums.org/showthread.php?t=1178490](http://ubuntuforums.org/showthread.php?t=1178490)

---

