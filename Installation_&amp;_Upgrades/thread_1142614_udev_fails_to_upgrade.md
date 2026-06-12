---
title: "udev fails to upgrade"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Ossipon on 2009-04-29
Hello,

After an aptitude upgrade, udev fails to configure:

```
Setting up udev (141-1.1) ...
 * Loading additional hardware drivers...udevadm trigger is not permitted while udev is unconfigured.
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing udev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up udev (141-1.1) ...
 * Loading additional hardware drivers...udevadm trigger is not permitted while udev is unconfigured.
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing udev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 udev
```


Searching the net, I found some users with a similar error, who got stuck in busybox after a reboot, so I'm a bit scared to do that. reinstalling udev does not work. removing udev is not an option because almost every other package depends on it.
I also tried to restart the "invoke-rc.d" script manually, but it fails. Strangely, restarting that script also fails on my other ubuntu machine, which does not have this problem. Does anyone have any ideas?

I'm running ubuntu server jaunty, kernel 2.6.28-11-server Amd64

---

### Post by andypi on 2010-01-13
Hey, I'm also currently having this problem in karmic. Did you ever manage to sort it out?

Andy

---

