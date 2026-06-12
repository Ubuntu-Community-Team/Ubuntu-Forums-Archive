---
title: "installed ati drivers - gui no longer loads"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Eonasdan on 2009-06-15
I just installed 9.04 (desktop). It was working pretty well and I was trying to find all my Windows replacement programs when I decided to install the ATI drivers (I have a Radeon HD 2600 Pro). After a reboot my pc was slow and unresponsive (which was the reason for changing in the first place), so I disabled the drivers and downloaded new drivers from ati. After installing the drivers and rebooting I got a mostly black screen with the ubuntu logo in strange colors and weird symbols at the top of the screen. Every few seconds the screen flashes and reappears. I have tried uninstalling the drivers, apt-get install --fix-broken dpkg-reconfigure -phigh xserver-org (may not work since I have desktop edition?) and deleting all the conf files out of the X11 folder...... help!

---

### Post by Eonasdan on 2009-06-16
<sarcasm>well thanks for the help</sarcasm> guess I'll just format and start over...

---

### Post by rogueleader12345 on 2009-06-16
Run the ati installer for the drivers. At the very end there will be a line that it says to put into a terminal if your screen blanks. Use it. It should work. I had the same problem, because I have an X1900 GT. I don't know how, you'll have to look around, but there's a way to get to a terminal instead of booting the GUI. If you'd like me to, I know someone I could ask, but that's up to you. :)

---

### Post by rogueleader12345 on 2009-06-16
Also, this link should help.
[http://k3mist.com/linux/ubuntu-jaunty-ati-restricted-proprietary-fglrx-driver-direct-rendering-mobility-radeon-hd-series/](http://k3mist.com/linux/ubuntu-jaunty-ati-restricted-proprietary-fglrx-driver-direct-rendering-mobility-radeon-hd-series/)

---

### Post by mhgsys on 2009-06-16
To get your display going again, 
Switch to console by pressing Ctrl+Alt+f1 (or f2,f3,f4,f5 etc)

then type;

```
 sudo /etc/init.d/gdm stop 
```

```

sudo dpkg-reconfigure xserver-xorg

```

```

sudo /etc/init.d/gdm start

```

---

### Post by Eonasdan on 2009-06-16
> **mhgsys said:**
> To get your display going again, 
Switch to console by pressing Ctrl+Alt+f1 (or f2,f3,f4,f5 etc)

then type;

```
 sudo /etc/init.d/gdm stop 
``````

sudo dpkg-reconfigure xserver-xorg

``````

sudo /etc/init.d/gdm start

```

didn't work. thanks though

> 
Also, this link should help.
[http://k3mist.com/linux/ubuntu-jaunt...eon-hd-series/]("http://k3mist.com/linux/ubuntu-jaunty-ati-restricted-proprietary-fglrx-driver-direct-rendering-mobility-radeon-hd-series/")

didn't work either

when I try apt-get purge xorg-driver-fglrx is says "pack is not installed so not removed" but if I type dpkg -l | grep fglrx it lists that as being there

---

### Post by Eonasdan on 2009-06-16
ok bit the bullet and reinstalled. I tried to install the ati drivers again. still no luck. tried it from the "hardware drivers" manager but after a reboot pc is slow and unresponsive. removed driver from use and now it won't let me split the monitor (duel screen) I only have "clone" as an option.

---

### Post by mk1w86 on 2009-06-16
The problem could be because your graphics card is one ATI have dropped support for.  There is an article on it here:

[http://tech.shantanugoel.com/2009/05/04/ubuntu-904-jaunty-jackalope-upgrade-graphics-problem.html](http://tech.shantanugoel.com/2009/05/04/ubuntu-904-jaunty-jackalope-upgrade-graphics-problem.html)

---

### Post by Eonasdan on 2009-06-16
[SIZE=2]ok if I install a [/SIZE][SIZE=2]NVIDIA Quadro NVS 290 P538 I've got laying around it boots but just gives me a black screen. I don't think I'll get approval to get a new GPU just to switch to linux
[/SIZE]

---

