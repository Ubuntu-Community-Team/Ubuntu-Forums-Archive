---
title: "Screen wont turn off after inactivity"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by navilon on 2005-07-28
the screen on my dell 5150 is set to shut off after about 20 minutes of inactivity.

in windows the screen shuts off completly
in ubuntu and other distros the screen turns to an off white/grey mixture as if the crystals behind it are bleeding.  ](*,) 

it doesnt look healthy. any ideas on how to get the monitor to shut off?

---

### Post by dave9191 on 2005-07-28
Try 

```
xset dpms force off
```

If it works you can add it to the config files. 

Dave

---

### Post by navilon on 2005-07-28
[QUOTE=dave9191]Try 

```
xset dpms force off
```

If it works you can add it to the config files. 

Dave[/QUOTE]
Thanks!  Where are the config files for that?

---

### Post by dave9191 on 2005-07-29
You can find the scripts in /etc/acpi. Different ones for different events. Also if you use Xscreensaver you can tell it to shut your monitor off. Run xscreensaver-demo, click on the advanced tab and enable power managment on the top left. that controls your monitor. 

Dave

---

