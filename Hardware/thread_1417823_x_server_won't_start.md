---
title: "x server won't start"
date: 2010-02-27
forum: Hardware
---

### Post by EngDrewman on 2010-02-27
I just installed Ubuntu 9.10 on a friend's Dell Latitude D800. 3D acceleration didn't work "out of the box," so I went into hardware drivers and installed the "recommended" Nvidia driver. After I restarted the computer, the xserver froze and won't load. How do I revert back to the generic driver via command line (and I don't know the name of the driver package, so "apt-get uninstall blah" won't work).

Already tried: sudo dpkg-reconfigure xserver-xorg and nothing happens.

---

### Post by EngDrewman on 2010-02-27
nevermind. Deleting the Xorg.conf file forced it to regenerate the default one.

---

