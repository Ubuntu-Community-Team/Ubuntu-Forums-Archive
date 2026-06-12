---
title: "How to install HP LaserJet P1102w printer in Ubuntu 19.04"
date: 2019-04-29
forum: Hardware
---

### Post by reginaldobertozzi on 2019-04-29
I can not install the HP LaserJet P1102w printer on Ubuntu 19.04.

I followed the commands of this link ([https://elias.praciano.com/2014/04/como-install-your-printer-hp-no-linux-usando-o-hplip/](https://elias.praciano.com/2014/04/como-install-your-printer-hp-no-linux-usando-o-hplip/)) but at the time that HP Device Manager opens - Plug-in Installer gives error ("plugin install failed") and does not install the plugin of this printer.

In this machine I have installed Kubuntu 18.04 LTS and I was able to install this printer.

I would like some help from this community to install this printer on Ubuntu 19.04.

Follow the terminal screen for analysis:
```


HP Linux Imaging and Printing System (ver 3.19.3)
Plugin Download and Install Utility ver. 2.1

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver 3.19.3)
Plugin Download and Install Utility ver. 2.1

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Checking for network connection ...
Downloading plug-in from:
Receiving digital keys: / usr / bin / gpg --homedir /home/reginaldo/.hplip/.gnupg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0x4ABA2F66DBD5A95894910E0673D770CDA59047B9
Creating directory plugin_tmp
Verifying archive integrity ... All good.
Uncompressing HPLIP 3.19.3 Self Extracting Archive Plugin ......................................... .....................

HP Linux Imaging and Printing System (ver 3.19.3)
Plugin Installer ver. 3.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Plug-in version: 3.19.3
Installed HPLIP version: 3.19.3
Number of files to install: 64

Plugin installation failed
error: Python gobject / dbus may be not installed
error: Plug-in install failed.

Done.

```

---

### Post by brian_p on 2019-04-30
Adapt [https://wiki.debian.org/PrintQueuesCUPS#hp](https://wiki.debian.org/PrintQueuesCUPS#hp) to your needs?

---

### Post by Autodave on 2019-04-30
Realize that the short term releases should be considered as beta releases: problems often occur either in the software or the upgrade process.  I would go back to 18.04 and live with that until 20.04 comes out.

---

