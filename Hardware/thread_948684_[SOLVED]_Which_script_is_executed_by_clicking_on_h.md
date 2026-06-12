---
title: "[SOLVED] Which script is executed by clicking on hibernate?"
date: 2008-10-15
forum: Hardware
---

### Post by DJTurboToJo on 2008-10-15
Hello Ubuntu community,

I was just thinking about what happens when I use my mouse to click on that exit button and afterwards on Hibernate. Well, everything works fine but I was just wondering which script or whatever is executed through this click.

When I use /etc/hibernate (which is the hibernate package that I first had to install) and also using /usr/sbin/hibernte (which I dont really know where it comes from) my laptop hibernates.

BUT when I use this my mouse to click on Hibernate, my laptop is doing a nice thing. After restarting (coming back from hibernation) it asks me for my password, which I think is quite necessary.

Any suggestions?

Thanks
TurboToJo

---

### Post by DJTurboToJo on 2008-10-15
Could that be the answer?

dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Hibernate

from: [http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f](http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f)

I m just not sure if that's really what happens by clicking on Hibernate.

---

### Post by pelle.k on 2008-10-15
Yes, gnome-power-manager does it, and the actual hibernation is done by this script (e.g. pm-hibernate + quirks and error checking);
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

---

### Post by DJTurboToJo on 2008-10-16
alrighty, thanks pelle.k

---

