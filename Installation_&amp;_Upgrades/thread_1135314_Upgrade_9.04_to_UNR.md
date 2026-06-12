---
title: "Upgrade 9.04 to UNR"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by jtnave23 on 2009-04-24
Dear all,
New to Ubuntu and have downloaded and installed 9.04 on my netbook to play and learn.  I would like to install Netbook Remix, but cannot seem to get it to work right with the install I've downloaded. Is there a way to upgrade to UNR via Terminal/Command lines? 
Thanks!
JN

---

### Post by GeorgeVita on 2009-04-24
Hi **jtnave23**,

as you have a running 9.04 on your netbook, you can install and then use the UNR desktop interface from the menu (on left of the top panel).

**System** > **Administration** > **Synaptic Package Manager** > give your password

click **reload** to have the latest data (you must have an internet connection active)

type **remix** on the **Quick search** window

**Mark** for installation (if not already installed) the following:
ubuntu-netbook-remix-default...
ubuntu-netbook-remix
netbook-launcher
desktop-switcher

**Apply** and download them to your system.

Switching can by done via **System** > **Preferences** > **Switch Desktop Mode**

A final **important** note: There is a bug in the switcher at the moment. In case you faced this problem described at:
[http://ubuntuforums.org/showthread.php?t=1135471](http://ubuntuforums.org/showthread.php?t=1135471)
you must know the solution!

Regards,
George

---

### Post by snowpine on 2009-04-24
Or, from the terminal:

```
sudo apt-get update
sudo apt-get install ubuntu-netbook-remix
```

---

### Post by Shidian Ou on 2009-04-24
I've upgraded the default desktop to 9.04, but when I search Synaptic for "remix", I don't get any of the "ubuntu-netbook-remix" packages.  I only get "netbook-desktop" ver. 1.6.20-0ubuntu2.  All the items are checked under the Ubuntu tab in the repositories.  Do I need to add a different rep?

[Update]
I don't know what happened, but I installed the netbook-launcher then relaunched Synaptic and now the Ubuntu-remix packages are there.

---

