---
title: "fluxbox"
date: 2005-01-06
forum: Installation &amp; Upgrades
---

### Post by dninja on 2005-01-06
Before I get into installing any of this, can anyone tell me if fluxbox or blackbox is available as a package (or whatever you call them in this distro)?

I've looked round to try to find a package list and can't find one. I looked at the ftp archive and couldn't find it in there.

---

### Post by Uuranor on 2005-01-06
Yes I have also fluxbox, and I'm installed it with Synaptic.
But I don't remember if it is avaiable on Warty (I use Hoary).

Why don't you compile it, if it is not present?

---

### Post by fng on 2005-01-06
```
fng@butters:~ $ sudo apt-cache search fluxbox
Password:
bbmail - Mail notifier for Blackbox
fbdesk - desktop icons for fluxbox window manager
fbpager - a pager application for the Fluxbox window manager
fluxbox - Highly configurable and low resource X11 Window manager
fluxconf - FluxBox configuration utility
wmfrog - WindowMaker dock app that shows your current weather
fng@butters:~ $ sudo apt-cache search blackbox | grep blackbox
bbdate - Date tool for the blackbox window manager
bblaunch - launch windows with manipulated attribs under blackbox
bbppp - PPP tool for the blackbox window manager
bbsload - System load tool for the blackbox window manager
bbtime - Time tool for the blackbox window manager
blackbox - Window manager for X
kblackbox - A simple logical game for the KDE project
waimea - A highly customizable window manager based on blackbox
fng@butters:~ $

``` 

Both are in the universe repository

---

### Post by dninja on 2005-01-06
right then, tonight will be ubuntu download and install night!

One other question, can I do the initial install without gnome?

---

### Post by Uuranor on 2005-01-06
I think not... Maybe with custom or minimal options at the  boot... 
I'm not sure. You can't select the packages during installation :(

---

### Post by puzzledm on 2005-01-18
Hi there just a few questions ....

How user friendly is fluxbox? - I have used KDE and Gnome only, but wouldn't mind messing around with some others.  I just wondered how steep the learning curve for it is.

Is configuring it straight forward? - Again it says it is extremely configurable but I know nothing about programming or much about command line work.

Thanks

---

