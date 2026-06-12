---
title: "how to install gnome on debian from internet"
date: 2008-12-02
forum: General Help
---

### Post by debianLAM on 2008-12-02
hi 
i installed the last version of debian testing on my machine and all installation steps was passed without any problem but when i finished the installation and rebooted the system it load only the text mode 
no graphical mode i tried install gdm that all passed good 
my problem until here is i cant install gnome from internet 
and my machine connected to lan and i want share internet connexion with machine on lan turned on windows xp 
please give me the good solution for that..

---

### Post by loomsen on 2008-12-02
Why exactly aren't you able to install gnome?

Run
```
ifconfig
``` 
to show your current network connections.

If you get lo as the only interface you might have to edit you 
```

sudo nano /etc/network/interfaces
```
and add your ethernet device. In most cases, at least in my case ^^, this interface is called eth0. So you gotta edit you interfaces file making it look sth like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

```

And make sure dhcp is enabled in your routers config.

Then, if you're online, run
(for a "lightweight" install)
```

sudo apt-get install gnome-core gnome-common
```
or, if you wanna have the standard package
```
sudo apt-get install gnome-desktop-environment
```
and for the full bloat(a lot of stuff!)
```
sudo apt-get install gnome
```
to pull the metapackages in.


If I got you wrong, and gnome is already installed, but not starting up,
try
```
sudo /etc/init.d/gdm start
```
from command line. If it starts up, edit 
```
sudo nano /etc/X11/default-display-manager
```
to make gdm the default.

The only line in this file should read:
```
/usr/sbin/gdm
```

---

