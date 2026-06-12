---
title: "Laptop wont work on battery in 9.10"
date: 2010-01-23
forum: Hardware
---

### Post by elbarto_87 on 2010-01-23
Hi All,

I have just installed 9.10 on an old samsung x20 I had lying around. Everything works perfectly apart from when I pull the power from the machine. If I pull the AC power, I get a breif popup saying battery is 1 hr 58mins or something like that then about 1 second later the screen fades and the machine hibernates/standby. I booted into windows and the battery works fine so I am in need of some advice on how to fix this problem in Linux.

Many Thanks,

Elbarto

---

### Post by mikewhatever on 2010-01-23
I was wondering, is 1 hour 58 minutes a reliable reading? Does the battery really lasts that long when running Windows?
Anyway, I don't know of a fix, but you can probably prevent the computer from hibernating as a workaround.

In Terminal, type **gconf-editor**, in the window that opens, navigate to **/apps/gnome-power-manager/actions**, click on 'critical_battery' and change the value next to it from 'hibernate' to 'nothing'.

---

### Post by elbarto_87 on 2010-01-23
Thanks Mate, I think you are pretty much on the money.

Just finished reading this:
[http://ubuntuforums.org/showthread.php?t=1341435](http://ubuntuforums.org/showthread.php?t=1341435)

It says to change the ac_lid settings to "nothing" in gconf-editor. Apparently disconnecting the battery has the same effect as closing the lid in my case.

It appears to be a good work around.

Regards ELbarto

---

