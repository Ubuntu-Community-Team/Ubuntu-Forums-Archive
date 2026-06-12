---
title: "battery applet remaining time"
date: 2010-01-14
forum: Hardware
---

### Post by irielion on 2010-01-14
Hi

In karmic I lost the feature of seeing how much time was left on my battery. While looking for a solution i found this commandline tool called IBAM. It has a better indication of the battery and it shows the time remaining. I wrote an applet for ibam to totally mimic gnome-power-manager applet. It even integrates with it's translations. Upon startup it will try to hide the gnome-power-manager applet, but you'll need my special patch one. Packages can be found in my ppa:
ppa:mark-baas123/ibam-applet

Greetings,

Mark ([https://launchpad.net/ibam-applet](https://launchpad.net/ibam-applet))

---

### Post by jaezcurra on 2010-01-18
Hi, it looks very interesting, but I actually cannot find how to install it

---

### Post by irielion on 2010-01-21
To install the applet open a terminal and write: 
```

sudo add-apt-repository ppa:mark-baas123/ibam-applet
sudo apt-get update
sudo apt-get install ibam-applet
```

---

### Post by MuddBuddha on 2010-11-13
Is the repository down?

---

### Post by irielion on 2010-11-14
Hi, after Karmic the ibam command line tool did no longer work due to changes in the kernel. Therefore the project died. Sorry.... 
Mark

---

