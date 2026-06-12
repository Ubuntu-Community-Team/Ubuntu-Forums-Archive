---
title: "VLC help"
date: 2008-07-28
forum: General Help
---

### Post by zerkk on 2008-07-28
I am trying to watch a video I downloaded earlier with VLC, and for some reason I get the video but no sound.

I can hear sound from other things just not VLC,

Thank you in advance for your help!

---

### Post by UbuntuNerd on 2008-07-28
try this 

install the vlc-plugin-pulse

if that doesn't work try this other 

vlc-plugin-esd

---

### Post by silkstone on 2008-07-28
Make sure you install all of these...

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot

then:

sudo /usr/share/doc/libdvdread3/install-css.sh

or if you get an error with that command:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by UbuntuNerd on 2008-07-28
also If you go to the package manager & do reload - mark all upgrades - apply, you'll find Ubuntu just release some upgrades to fix this problem.

---

### Post by joshzam on 2008-08-01
> **UbuntuNerd said:**
> try this 

install the vlc-plugin-pulse

if that doesn't work try this other 

vlc-plugin-esd

OMG, this is absolutely what I've been searching for!

I installed the Pulse plugin and, when nothing happened, I went back and actually read the package description in Synaptic and it mentioned how you need to choose the Pulse plugin from the Tools > Preferences > Audio > Output > Type dropdown before it will take effect (duh!).

Thanks, Nerd!

---

