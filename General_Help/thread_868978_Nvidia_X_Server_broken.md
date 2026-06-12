---
title: "Nvidia X Server broken"
date: 2008-07-24
forum: General Help
---

### Post by knudsenjoe on 2008-07-24
I can't change the my screen resolution. I'm using the Nvidia 'latest cards' driver. This was previously working, and I think maybe the Linux kernel update to xxxxxxx.19 may have broken it. Any help will be much apprecitated

---

### Post by jimv on 2008-07-24
Use EnvyNG to install the driver.  Here's the console commands:

```
sudo apt-get install envyng-gtk
envyng -t
```

Press 1 to install the driver.

Envy also keeps your driver up to date with kernel upgrades, so hopefully you won't have to do this again.

---

### Post by tuxxy on 2008-07-24
Try disabling/restarting the driver from hardware drivers, If the driver will not function at all you could use Envyng to try and install, if no luck you could also try reconfiguer xorg 

make a backup copy of your /etc/X11/xorg.conf 

```

cd /etc/X11
sudo cp xorg.conf xorg.conf.back
```

Then try to reconfigure your xserver-xorg
```

sudo dpkg-reconfigure xserver-xorg
```

If someone goes wrong simpy use the backup xorg

```
cd /etc/X11
sudo cp xorg.conf.back xorg.conf

```

---

### Post by knudsenjoe on 2008-07-24
I tried the first one, doing the envy install thing. It installed a bunch of stuff. Afterwards it gave me an error about Xrandrx or something (sorry i don't have specifics).

The second method has me now in a 800x600 resolution, and now I don't even have the higher resolutions available as an option.

---

### Post by knudsenjoe on 2008-07-24
bump

---

### Post by evertmantel on 2008-07-24
Hi,
gksudo nvidia-settings 

Had the same problem, and this worked well for me.

---

### Post by knudsenjoe on 2008-07-24
tried the nvidia setting thing, it told me to do nvidia-xconf

still stuck at 800x600

---

### Post by evertmantel on 2008-07-24
you'll have to install the program first from the repositories:

do a search on the synaptic manager for 'nvidia-settings'
install it
do the gksudo nvidia-settings -thingy

---

### Post by knudsenjoe on 2008-07-24
I've got the nvidia settings manager, but it tells me i don't have the nvidia xdriver.

---

### Post by knudsenjoe on 2008-07-24
oops, spilled my beer

---

