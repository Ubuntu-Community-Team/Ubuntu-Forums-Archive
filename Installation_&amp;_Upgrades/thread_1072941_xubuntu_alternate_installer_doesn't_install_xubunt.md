---
title: "xubuntu alternate installer doesn't install xubuntu"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by dcottingham on 2009-02-17
I just ran the xubuntu 8.10 alternate installer on a computer, get to the reboot, and am astonished to be staring at a dumb terminal. I look in /var/log, there is no Xorg.0.log.  I look in /etc/X11, there is no xorg.conf, not even the empty one that seems to be the latest fashion.  I can find no evidence that the installer made any attempt to set up an X desktop.

So I started the installation over from scratch, and this time when I get to the screen that lists a few optional components (print server, mail server, ...) I check the box for kubuntu desktop.  Now when we get to the reboot, I find myself looking at a kubuntu desktop.  On the login screen I have the choice of "default", "KDE", or "Failsafe".

So from the xubuntu installer I have a working kubuntu desktop, but I can't seem to get any xubuntu desktop.  Any ideas what's going wrong?

Perhaps a related question -- somewhere towards the end of the installation it says something about gathering info for an installation report.  Where can I find this report?

Thanks.

---

### Post by spcwingo on 2009-02-17
Press ALT+F1 and enter:

```
sudo apt-get remove --purge kubuntu-desktop && sudo apt-get install xubuntu-desktop
```

followed by:

```
sudo reboot
```

This should at least remove the Kubuntu desktop and install the Xubuntu desktop.  As far as why it did what it did...I am at a loss.  :-k  I've never seen that at all.

---

### Post by dcottingham on 2009-02-18
Thanks, that fixed it.  To make my life more difficult, I instead did a fresh install w/o asking for the kubuntu desktop, then asked aptitude to install xubuntu-desktop.  800+ packages later, it's working just fine.

---

