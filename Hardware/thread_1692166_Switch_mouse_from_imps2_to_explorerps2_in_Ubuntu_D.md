---
title: "Switch mouse from imps/2 to explorerps/2 in Ubuntu Desktop 10.10 64-bit"
date: 2011-02-21
forum: Hardware
---

### Post by dualityim on 2011-02-21
I'm using Ubuntu Desktop 10.10 64-bit inside VMware Workstation on a Windows 7 64-bit host. I have a 5-button mouse with forward and back buttons which do not work inside the VM. Only the three main buttons work. I stumbled upon this page: [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools) which suggests that changing the mouse type from imps/2 to explorerps/2 in xorg.conf might allow the additional buttons to work. The problem is, it seems in Ubuntu 10.10 there is no xorg.conf, everything is configured automatically. Is there a way to specify a xorg.conf setting on a system that doesn't have that file? Or would I need to create a xorg.conf file manually? Thanks.

---

### Post by dualityim on 2011-02-21
I decided to generate an xorg.conf using Xorg -configure and edited the mouse entry to use the ExplorerPS/2 protocol. However after rebooting, the mouse is still listed as ImPS/2 Generic Wheel Mouse when I use the "xinput list" command. It seems the xorg.conf file is not being used and Ubuntu is still using auto detection for X settings. How do I force the system to use my custon xorg.conf file?

---

