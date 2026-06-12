---
title: "Gutsy w/ Dell Latitude D430"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by mikawber on 2007-10-22
I got a new laptop about 2 weeks ago and decided that I'd try Gutsy on it before I put it on my main machine. Everything is working great except two minor, yet annoying, issues.

1) The system beep won't turn off. I've tried  sudo rmmod pcspkr and it only works until I turn the computer off. This is especially annoying when sitting in class. 

2) It takes about 20-30 seconds to show the desktop after I log in. I haven't done any troubleshooting with this issues because I have no idea where to begin. 

If anyone could help with either of these issues, I'd greatly appreciate it. Thanks in advance.

---

### Post by mikawber on 2007-10-23
Could someone at least help me with turning the internal system beep off? Is there another command I can try to make it permanant?

---

### Post by trjnhrse44 on 2007-10-23
add the line:
blacklist pcspkr
to the end of your blacklist modules file

```
sudo gedit /etc/modprobe.d/blacklist
```

in a terminal to open the file
save and close then restart the machine
spkr will be off unless you manually modprobe pcspkr

---

### Post by mikawber on 2007-10-24
thanks that worked perfectly, any ideas on the other issue?

---

### Post by trjnhrse44 on 2007-10-24
No, I would need more info.
Has this always been the case?
Is this from a fresh install or an upgrade?
What programs are listed for startup under System, Preferences, Sessions?

---

### Post by mikawber on 2007-10-25
> **trjnhrse44 said:**
> No, I would need more info.
Has this always been the case?
Is this from a fresh install or an upgrade?
What programs are listed for startup under System, Preferences, Sessions?

This is a fresh install and has happened ever since the install. Below is the list of programs set for startup:

Bluetooth Manager
Evolution Alarm Notifier
Network Manager
Power Manager
Print Queue Applet
Restricted Drivers Manager
Tracker
Update Notifier
User update folder
Visual
Volume Manager

---

### Post by mikawber on 2007-10-25
oh yeah I forgot to say that there is no splash screen either

---

