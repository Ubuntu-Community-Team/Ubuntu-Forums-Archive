---
title: "Dell XPS M1530 - problems rebooting/powering down"
date: 2008-12-27
forum: Hardware
---

### Post by finster on 2008-12-27
Hi all,

I have a Dell XPS M1530 laptop (with nVidia 8600M GT graphics). I've installed Ubuntu 8.10 and nearly everything works fine, including suspend & resume when the lid is opened/closed. However I am having problems when doing a power off or reboot - the system crashes just showing a mostly white screen that slowly fades to black.

This didn't happen from a fresh install - it just seems to have started to happen from after I installed some updates.

I'm not sure where to look. I can't see anything helpful in /var/log/messages, the last few lines are: -

```
Dec 22 23:42:27 xps kernel: [ 1305.955084] Registered led device: iwl-phy0:TX
Dec 22 23:43:05 xps bonobo-activation-server (andy-11517): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Wv7LtIrv2Y: Connection refused
Dec 22 23:43:11 xps kernel: [ 1349.382643] apm: BIOS not found.
Dec 22 23:43:12 xps kernel: [ 1350.838987] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 23:43:14 xps kernel: [ 1353.116165] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x20171704
```

I've also had a look in /var/log/Xorg.0.log.old, the last few lines are: -

```
(II) UnloadModule: "evdev"
(II) Broadcom Corp: Close
(II) UnloadModule: "evdev"
(II) Broadcom Corp: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
```

Does anybody have any ideas?

Thanks.

---

