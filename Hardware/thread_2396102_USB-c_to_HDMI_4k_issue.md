---
title: "USB-c to HDMI 4k issue"
date: 2018-07-11
forum: Hardware
---

### Post by shalashasks on 2018-07-11
Hi all,

I have a Dell XPS 13 running Ubuntu 18.04. I have a 4k external monitor that is connected to the laptop through a HDMI to USB-c adapter. The external monitor was working fine (running 4k @ 60 Hz) up until this week, when it just stopped working. Now, whenever I plug any monitor in to the laptop via USB-c, the laptop registers the monitor, but the monitor will either not display anything and go to sleep, or will only allow me to display up to a resolution of 1920x1080 - I don't suppose anyone else has been having a similar issue recently? Attached is a screenshot of running tail -f /var/log/syslog just before connecting the monitor.

[ATTACH=CONFIG]280354[/ATTACH][ATTACH=CONFIG]280355[/ATTACH]

---

### Post by shalashasks on 2018-07-11
Quick update on this - I've switched my HDMI to USB-c adapter for a spare one I had in my office, and I'm now back up to running 4k but limited to 30 Hz. Switching back to the old adapter results in the same issues I was having previously.

---

