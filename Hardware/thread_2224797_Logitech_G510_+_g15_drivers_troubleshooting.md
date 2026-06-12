---
title: "Logitech G510 + g15 drivers troubleshooting"
date: 2014-05-18
forum: Hardware
---

### Post by jcllings on 2014-05-18
1st problem: You try to install g15daemon and you get:
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g1

This seems to have been fixed by:
```
sudo ln -s /dev/uinput /dev/input/uinput
```

...however the next problem is:

```
Setting up g15daemon (1.9.5.3-8.2ubuntu3) ...
Starting g15daemon: invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing package g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
***@*********:/dev/input$ 
```

...or:

```
***@*********:sudo dpkg --debug=2000 --configure -a 
Setting up g15daemon (1.9.5.3-8.2ubuntu3) ...
Starting g15daemon: invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing package g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon

```

Question: What's my next move?  How do I get more verbose output from dpkg if --debug=2000 is the maximum debug setting?

---

### Post by jcllings on 2014-05-18
OK, so gnome15 seems to work better than the g15daemon but I still have a problem - My media keys don't work. Everything else seems to.

---

