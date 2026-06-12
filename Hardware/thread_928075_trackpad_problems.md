---
title: "trackpad problems"
date: 2008-09-23
forum: Hardware
---

### Post by dlm4849 on 2008-09-23
I have been having issues with my trackpad freaking out and becoming extremely jumpy and acting like Im tapping it when im not even touching it anymore. This is a lenovo R61. If anyone has any insight, please share.

Thanks

---

### Post by dlm4849 on 2008-11-07
bump, still having issues even after a fresh install

---

### Post by wgrant on 2008-11-07
Which release of Ubuntu are you using? Please attach /etc/X11/xorg.conf and /var/log/Xorg.0.log after it has happened.

---

### Post by dlm4849 on 2008-11-08
using 8.04...8.10 and the nvidia 140m in my thinkpad didn't want to get along, but that's a whole 'nother thread.

Here's my xorg.conf and the xorg log file. I scanned through and didnt see any time sensitive data, but if it helps, it last happened about an hour and a half ago.

Thanks

---

### Post by dlm4849 on 2008-11-08
To try and better convey what is happening...it almost seems like the pad thinks that there are two fingers on the pad when im positive there aren't and the it seems to interpret any attempts at movement as a tap, therefor, a click.

---

### Post by dlm4849 on 2008-11-08
Just happened again, so heres a new log file.

---

### Post by dlm4849 on 2008-11-11
Anyone?

---

### Post by JinStevens on 2008-11-11
I had the exact same problem and here's the link to the place where I found the solution:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Search for the term "touchpad" on that page.

The key part is to add this line in your xorg.conf file:

Option "SHMConfig" "true

There's a second step too and it's configure your sessions.

> Now, navigate to System > Preferences > Sessions and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

---

### Post by dlm4849 on 2008-11-11
Thanks. Ill report back on whether or not this works. (I cant seem to make the problem occur with any consistency.)

---

