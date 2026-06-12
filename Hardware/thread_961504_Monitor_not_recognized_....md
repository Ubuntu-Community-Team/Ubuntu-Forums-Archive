---
title: "Monitor not recognized ..."
date: 2008-10-28
forum: Hardware
---

### Post by muddi900 on 2008-10-28
First time linux user here. I tried the ubuntu live CD first to check if my Hardware is compatible. At that time, Ubuntu recognized my monitor(Viewsonic VA1912w) just fine, running at native res(1440x900). But when I tried the Wubi install, it doesn't recognise it any more.


What should I do??

---

### Post by overdrank on 2008-10-28
> **muddi900 said:**
> First time linux user here. I tried the ubuntu live CD first to check if my Hardware is compatible. At that time, Ubuntu recognized my monitor(Viewsonic VA1912w) just fine, running at native res(1440x900). But when I tried the Wubi install, it doesn't recognise it any more.


What should I do??

Hi and welcome, have you tried using the alt, F2 keys and enter the command 
```
gksu displayconfig-gtk
``` and adjust the monitor

---

### Post by muddi900 on 2008-10-28
I was in windows. So I rebooted to try your solution and the screen went blank after the splash screen. It probably has to do with my graphic card driver notbeing installed, but it was working 15 minutes ago!

edit: back in ubuntu. It suddenly works. but the above solution doesn't work, nothing happens.

---

### Post by muddi900 on 2008-10-28
Somebody? Anybody?

---

### Post by overdrank on 2008-10-29
> **muddi900 said:**
> I was in windows. So I rebooted to try your solution and the screen went blank after the splash screen. It probably has to do with my graphic card driver notbeing installed, but it was working 15 minutes ago!

edit: back in ubuntu. It suddenly works. but the above solution doesn't work, nothing happens.

Ok if nothing happens you may need to install. Go to synaptic manager and install displayconfig-gtk. 
What is the model of the graphics card. You can use the command lspci in the terminal located under applications, accessories, terminal. Then look for VGA to identify your graphics card.

---

### Post by muddi900 on 2008-10-29
> **overdrank said:**
> Ok if nothing happens you may need to install. Go to synaptic manager and install displayconfig-gtk. 
What is the model of the graphics card. You can use the command lspci in the terminal located under applications, accessories, terminal. Then look for VGA to identify your graphics card.
Sorry no displayconfig-gtk comes up when I search Synaptic. I also tried APT, I got this:

```
Package displayconfig-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package displayconfig-gtk has no installation candidate

```

---

### Post by muddi900 on 2008-10-29
I installed the driver for my graphic card using ati linux driver wiki. It is a Radeon HD4850. While the instalation process was smooth, when I rebooted, I got wierd messages about configuring my display and the screen got garbled. so I rebooted again and now ubuntu recognizes my monitor, but it does not recognize my graphic card. I want 3d acceleration damnit!

you can aad the solved tag.

---

