---
title: "install notify-osd on my xubuntu jaunty?"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by saketh on 2009-07-29
any idea how to setup notify-osd on my xubuntu jaunty?
i tried 'sudo apt-get install notify-osd" and added

"
#!/bin/bash
killall notification-daemon
sleep 1
~/.notify-osd/src/notify-osd
"

the volume notifications dont come up and neither do the internet ones or the power ones.

thanx :)
saketh

---

### Post by Vinze on 2009-08-25
Unfortunately, Xfce isn't supported for those notifications. Steve Dodier is hard at work at making those work for 9.10, but for now, you'll have to do without those.

---

### Post by fchristophersen on 2009-12-18
i did manage to install it in xubuntu jaunty...

it's quite simple, all you have to do is:

1. install notify-osd in synaptic
2. download the following **_karmic_** packages from ubuntu packages site (packages.ubuntu.com), and install them with gdebi:
notify-osd-icons_0.3_all.deb
libxcb-keysyms1_0.3.6-1_i386.deb
xfce4-volumed_0.1.4-0ubuntu1_i386.deb
3. add /usr/lib/notify-osd/notify-osd to startup
4. enjoy!

i hope it works for you too... good luck!

---

