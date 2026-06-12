---
title: "Eagle-usb in dapper"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by mtc on 2006-02-03
I have just updated from breezy to dapper, and after that the system doesn't see my modem (Sagem f@st800). The eagle-usb kernel module is loading without any problems, but whenever I try to execute eaglectrl I get a message that no device was found.
The only idea I have is that upgrade to dapper caused removing hotplug and I need to do something in configuration of udev.
Can anybody tell me how do I fix it?

---

### Post by badmad on 2006-02-06
there are 2 problems: first if you want eagle with 2.6.15 you need to use cvs version, second is that eaglectrl couldn't found entry at /proc/bus/usb/X/Y (it's in /proc/drivers/eagle-usb/X-Y) so it's a problem with udev/procps. (udev has a compatibility mode with hotplug but it is not set in ubuntu?)

I've menaged to run it by forcing installing hotplug, running it and it created desired entry, but you need to do it every time: from root: dpkg -i --force-conflicts <hotplug.deb> , then /etc/init.d/hotplug start, eaglectrl -d; staratdsl.

but then when I run apt-get update & upgrade it uninstalls hotplug since it's deprecated

so to sum up: cvs eagle-usb (or uagle-atm currently bundled with mm patchset, but it suck, especially with configuration) & correct entry at /proc/bus/usb (as I said it's probably udev problem, but I didn't menage to write a correct rule)

I hope it will be fixed. Cheers

---

