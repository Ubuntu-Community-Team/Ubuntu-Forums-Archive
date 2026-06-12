---
title: "cdemu HELP!"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by phatbastard on 2009-06-05
I cant for the life of me get the cdemu daemon to start. I am using Kubuntu jaunty.

phatbastard@phatbastard-desktop:~$ cdemu -b system status
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon (bus: 'system')!
phatbastard@phatbastard-desktop:~$ cdemud -s
Failed to parse options: Unknown option -s
phatbastard@phatbastard-desktop:~$ cdemud
Starting daemon in local mode with following parameters:
 - num devices: 1
 - ctl device: /dev/vhba_ctl
 - audio driver: null
 - bus type: system
cdemud: cdemud_daemon_initialize: failed to request name on system bus!
Daemon initialization failed: Name request on D-BUS failed.

---

