---
title: "ubuntu extracting to winxp"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by cogs10 on 2009-06-09
hey there! since i'm having so much trouble with my install (don't even know what to call ubuntu that installs into windowsxp and dual boots); is there any easier way to intall with winxp besides an iso burned to disk? i can't get that to work very well. can't i just download the files and have them work on boot, without a disk or usb? like, can't the files already be extracted to windows, and have it install on the hard disk? (i'm installing ubuntu within winxp, not a standalone ubuntu). thank you, cogs

---

### Post by presence1960 on 2009-06-09
> **cogs10 said:**
> hey there! since i'm having so much trouble with my install (don't even know what to call ubuntu that installs into windowsxp and dual boots); is there any easier way to intall with winxp besides an iso burned to disk? i can't get that to work very well. can't i just download the files and have them work on boot, without a disk or usb? like, can't the files already be extracted to windows, and have it install on the hard disk? (i'm installing ubuntu within winxp, not a standalone ubuntu). thank you, cogs

if you can be more precise and describe the exact trouble you are having we can begin to help you.

---

### Post by #11u-max on 2009-06-09
if you mean a virtual machine, you can mount your iso file to your virtual machine.

---

### Post by lisati on 2009-06-09
The usual method of installing ubuntu is to burn it to CD or DvD
Hopefully one of the following links will provide you some ideas and some alternatives to burning to CD

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by cogs10 on 2009-06-10
ding ding ding, #11u-max gets the prize! virtual box and xubuntu8.10 is now installed on my winxp.  it connects to the internet, and has no errors on boot. the only thing is that it's slow, cause i only have 384mb ram. and i don't know how to use virtualbox very well, so i'll have to learn. but i learned dosbox, so it can't be any harder.
 
this comes after 2 weeks of trying to make xubuntu load (avahi kept failing, and i had no keyboard or mouse due to the consequetial failure of dbus and hal). i will probably never find the answer, but the closest i've come is that avahi is connected to dbus, when it should not be.
here's the link that started the problem: 
[http://lists.freedesktop.org/archives/avahi/2005-June/000003.html](http://lists.freedesktop.org/archives/avahi/2005-June/000003.html)
and here's the bug report:
[https://bugs.launchpad.net/ubuntu/karmic/+source/avahi/+bug/327362](https://bugs.launchpad.net/ubuntu/karmic/+source/avahi/+bug/327362)

---

