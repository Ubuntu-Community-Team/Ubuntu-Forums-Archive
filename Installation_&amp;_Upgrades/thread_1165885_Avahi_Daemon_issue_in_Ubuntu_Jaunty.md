---
title: "Avahi Daemon issue in Ubuntu Jaunty"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by dipaish on 2009-05-21
To get rid of avahi network error each time you boot your computer follow the following steps:

Go to the terminal and type 

sudo sed -i -e'/AVAHI_DAEMON_DETECT_LOCAL/s/1/0/' /etc/default/avahi-daemon

and then restart your avahi daemon

sudo service avahi-daemon restart

Next time you boot your computer you won't get any network error message.

cheers ;)

---

