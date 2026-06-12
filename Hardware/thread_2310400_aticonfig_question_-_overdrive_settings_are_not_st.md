---
title: "aticonfig question - overdrive settings are not sticking after reboot"
date: 2016-01-18
forum: Hardware
---

### Post by maxinstuff2 on 2016-01-18
I am using aticonfig overdrive functions to overclock my GPU, and I can set the core and memory clocks with (for example):
```
sudo aticonfig --odsc 1200,1400
```

This works fine, it sets the core clocks to 1200 and leaves the memory clocks at 1400 (the stock speed). This seems to be a stable overclock for me - so I commit the changes with:
```
sudo aticonfig --odcc
```
And I will get a confirmation that this has been comitted. Now, according to the documentation (aticonfig --help) this commits the clock so that they will stick when X is restarted. These setting DO survive a restart of X, via logout/login or via restarting the lightdm service. BUT, the settings do NOT survive a reboot.

The first thing I tried to do was find out where these settings were going - but I cannot find them anywhere in /etc/X11...... xorg.conf is left completely unchanged during this whole process and nothing is created in xorg.conf.d either.....

Does anyone have any idea where the aticonfig settings go? Or why changes to them are wiped/dropped when the system restarts?

Hardware in my signature. I am running Kubuntu 14.04, fully updated, with the fglrx-updates driver from the repos.

---

