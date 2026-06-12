---
title: "Dual Monitors Twinview overwrites xorg.file to xorg.conf.failsafe.bk"
date: 2008-08-11
forum: General Help
---

### Post by jwferk on 2008-08-11
I've got an issue with the NVIDIA 173* driver I use for dual monitors in Hardy.  Every third or fourth boot the driver fails and I go into the default Ubuntu low resolution single monitor mode.  I need to reload the NVIDIA driver to get dual monitors back.

What seems to be going on is at boot a new file named xorg.conf.failsafe.bk is being written to X11.  This is in addition to the working xorg.conf and the xorg.conf.backup file (written by the NVIDIA driver at installation).  

I can't figure out how to stop the xorg.conf.failsafe file from being written.

The only thing I've linked this behavior too is that it seems to happen more often after I install StartUpManager.

Suggestions?  Thanks.

---

