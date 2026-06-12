---
title: "Need &quot;via&quot; kernel module for Epia CLE266"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by t.schutter on 2005-04-08
I am running Hoary Array-5 on a VIA Epia box with an onboard CLE266
video.  The driver is the "via" driver, which was automatically
selected during install.  I am trying to enable DRI so that Mythtv can
use the MPEG2 decoder.  But it appears that I am missing the "via"
kernel module.  I have found some info on the net, but nothing that
seems to fit the Ubuntu/Xorg model.

From /var/log/Xorg.0.log:
  ...
  (II) LoadModule: "via"
  (II) Loading /usr/X11R6/lib/modules/drivers/via_drv.o
  (II) Module via: vendor="X.Org Foundation"
          compiled for 4.3.99.902, module version = 0.0.0
          Module class: X.Org Video Driver
          ABI class: X.Org Video Driver, version 0.7
  ...
  drmOpenDevice: node name is /dev/dri/card0
  drmOpenDevice: open result is -1, (Unknown error 999)
  drmOpenDevice: open result is -1, (Unknown error 999)
  drmOpenDevice: Open failed
  drmOpenDevice: node name is /dev/dri/card0
  drmOpenDevice: open result is -1, (Unknown error 999)
  drmOpenDevice: open result is -1, (Unknown error 999)
  drmOpenDevice: Open failed
  [drm] failed to load kernel module "via"
  (II) VIA(0): [drm] drmOpen failed
  (EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.

Thanks,
Tom

---

### Post by nad on 2005-04-08
There is currently no support for DRI with the CastleRock chip. There should be a notice in your xorg log about an unknow card ID. Please notify the unichrome group at sourceforge.net that they may begin to add support for it. You do have 3DNow and XAA.

Dan M

---

### Post by chrisg67 on 2005-04-18
I'm currently building a MII 12000 ubuntu machine (also uses CLE266 drivers). I found the VeXP project at sourceforge [http://sourceforge.net/projects/viaexp/](http://sourceforge.net/projects/viaexp/). This might be of help to you.

I've not got around to installing it yet, hope to do so soon though.

---

### Post by k4p0w3r on 2005-12-07
Hi all,

Managed to get DRI to work in Breezy 5.10. I made a wiki for this here:

[https://wiki.ubuntu.com/ViaEpiaDriHowto](https://wiki.ubuntu.com/ViaEpiaDriHowto)

---

### Post by Swab on 2006-01-28
I followed the wiki guide but wasn't able to boot... getting the following error:

VFS: Cannot open root device "hda1" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing : VFS: Unbale to mount root fs on unknown-block(0,0)

---

