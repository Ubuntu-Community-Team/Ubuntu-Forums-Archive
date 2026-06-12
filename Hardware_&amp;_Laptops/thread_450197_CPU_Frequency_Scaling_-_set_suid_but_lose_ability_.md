---
title: "CPU Frequency Scaling - set suid but lose ability to change from time to time"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Barnable on 2007-05-21
I did the whole set suid bit (Ubuntu Feisty - $ sudo dpkg-reconfigure gnome-applets and answered “Yes” to the question regarding setting the suid of the cpufreq-selector executable) and it works fine *most of the time*.

From time to time, however, I click on the applet and it *won't* change whatever I click on.

In all fairness, I've noticed it more often when I'm trying to get updates or using Synaptic or some other process where I've used sudo/entered my password to give a process root privileges.

Is this likely to be connected?

Thanks,

B.

---

### Post by Barnable on 2007-05-23
Update on this.

My box is a Fujitsu Siemens Amilo PA1510 laptop, running Feisty.

I now cannot change CPU frequency at all, using either the applet or by forcing it in the command line - it just stays at 800MHz (on a 1.8MHz AMD dual core processor).

Last night it was pootling along - not doing anything draining - and the fans started roaring, and it switched itself off.  Couldn't turn it back on using battery power, but it turned on when plugged into mains.

Battery meter had been fine and no warnings had been given, but when plugged into the mains it reported that the battery was at 0% and charging.

Am going to reinstall Feisty tonight to see what happens, but am wondering whether this could be a hardware issue rather than software?

Anyone have any thoughts on this? :confused:

Thanks,

B.

---

