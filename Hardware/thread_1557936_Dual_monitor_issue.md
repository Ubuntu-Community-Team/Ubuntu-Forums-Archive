---
title: "Dual monitor issue"
date: 2010-08-21
forum: Hardware
---

### Post by M0GEJ on 2010-08-21
Have just installed a second monitor (not the same type as the first).  What is appearing on the new monitor is exactly the same as on the other one.  

On the display settings there is only one screen listed.  I also get the following error message:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Any ideas?

---

### Post by dino99 on 2010-08-21
install this ppa to synaptic repo tab:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

remove xorg.conf: sudo rm -f /etc/X11/xorg.conf

update and install the needed packages (nvidia-current, ....)

then reboot and check driver activation: system admin hardware driver, nvidia-current might be activated

then run nvidia-xconfig: system admin nvidia x settings, if it cant set the good settings (for each monitor), then you need to tweak the new xorg.conf created

---

### Post by M0GEJ on 2010-08-21
Tried doing that but encountered a few problems
[HTML]then reboot and check driver activation: system admin hardware driver, nvidia-current might be activated[/HTML]
Here there was no change to the installed drivers

[HTML]then run nvidia-xconfig: system admin nvidia x settings, if it cant set the good settings (for each monitor), then you need to tweak the new xorg.conf created[/HTML]
The nvidia option has now disappeared from the menu:(

Am currently trying to figure out where I made the mistake...

---

