---
title: "Upgrade-manager freeze [solved?]"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by redxine on 2009-05-01
I finally got the time to hit 'upgrade' and install the Gigabyte-worth of software to upgrade to jaunty from intrepid. The manager started up and then came up with a message saying "Software sources have changed.... you may need to re-enable them...", but the entire window was non responsive. Had to force quit with xkill. So I reboot and try again. Different message: "Do you want to accept this huge piece of software?" And same result. Frozen. Two reboots later, and while receiving the same result, I realize my panel becomes non-responsive along with the upgrade manager, so I switch over to TTY2 and run a 'killall gnome-panel'. And it fixed it!

---

### Post by cariboo on 2009-05-01
Do you have any ppa's or third party repositories enabled? if you do open /etc/apt/sources.list and add a # to the start of any ppa or third party repositories. Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

this opens the sources.list file as root, and allows you to edit it.

---

### Post by redxine on 2009-05-02
Nothing wrong with the sources. all third parties were cancelled out during the upgrade. I'm seeing some other problems with gnome, synaptics, X, usplash, admin authentication.... I think I'll reinstall from CD.

---

