---
title: "Booting hangs after update - sound card issue"
date: 2014-06-30
forum: Hardware
---

### Post by daniel10a on 2014-06-30
Hi everyone,
I have a big problem with my on-board sound card.
After last update I cannot boot Ubuntu properly - it hangs with the following errors (recovery mode) 
[IMG]http://i58.tinypic.com/2eebudi.jpg[/IMG]

When I disable on-board sound card in BIOS, the system runs without any problems.

This is the note from /var/log/apt/history.log file
```
Start-Date: 2014-06-27  12:17:35Commandline: aptdaemon role='role-commit-packages' sender=':1.580'
Install: linux-image-extra-3.13.0-30-generic:amd64 (3.13.0-30.54), linux-image-3.13.0-30-generic:amd64 (3.13.0-30.54), linux-headers-3.13.0-30-generic:amd64 (3.13.0-30.54), linux-headers-3.13.0-30:amd64 (3.13.0-30.54)
Upgrade: oem-audio-hda-daily-dkms:amd64 (0.201406181447~ubuntu14.04.1, 0.201406261608~ubuntu14.04.1), hplip:amd64 (3.14.3-0ubuntu3, 3.14.3-0ubuntu3.2), linux-headers-generic:amd64 (3.13.0.29.35, 3.13.0.30.36), resolvconf:amd64 (1.69ubuntu1, 1.69ubuntu1.1), python-samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.1, 4.1.6+dfsg-1ubuntu2.14.04.2), telepathy-gabble:amd64 (0.18.2-1, 0.18.3-0ubuntu0.1), libsane-hpaio:amd64 (3.14.3-0ubuntu3, 3.14.3-0ubuntu3.2), libapache2-mod-php5:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), php5-mysql:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), php5-common:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), php5-curl:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), libjavascriptcoregtk-3.0-0:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), libwebkitgtk-1.0-0:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), gir1.2-javascriptcoregtk-3.0:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), libhpmud0:amd64 (3.14.3-0ubuntu3, 3.14.3-0ubuntu3.2), php5-readline:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), php5:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), gnupg:amd64 (1.4.16-1ubuntu2, 1.4.16-1ubuntu2.1), printer-driver-postscript-hp:amd64 (3.14.3-0ubuntu3, 3.14.3-0ubuntu3.2), libgphoto2-port10:amd64 (2.5.3.1-1ubuntu2, 2.5.3.1-1ubuntu2.2), samba-common-bin:amd64 (4.1.6+dfsg-1ubuntu2.14.04.1, 4.1.6+dfsg-1ubuntu2.14.04.2), php5-cgi:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), libwebkitgtk-3.0-0:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), samba-libs:amd64 (4.1.6+dfsg-1ubuntu2.14.04.1, 4.1.6+dfsg-1ubuntu2.14.04.2), php5-cli:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), libgphoto2-6:amd64 (2.5.3.1-1ubuntu2, 2.5.3.1-1ubuntu2.2), smbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.1, 4.1.6+dfsg-1ubuntu2.14.04.2), printer-driver-hpcups:amd64 (3.14.3-0ubuntu3, 3.14.3-0ubuntu3.2), gpgv:amd64 (1.4.16-1ubuntu2, 1.4.16-1ubuntu2.1), linux-firmware:amd64 (1.127.2, 1.127.4), libwebkitgtk-3.0-common:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), libwebkitgtk-1.0-common:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), hplip-data:amd64 (3.14.3-0ubuntu3, 3.14.3-0ubuntu3.2), libwbclient0:amd64 (4.1.6+dfsg-1ubuntu2.14.04.1, 4.1.6+dfsg-1ubuntu2.14.04.2), linux-libc-dev:amd64 (3.13.0-29.53, 3.13.0-30.54), libjavascriptcoregtk-1.0-0:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), php5-gd:amd64 (5.5.9+dfsg-1ubuntu4.1, 5.5.9+dfsg-1ubuntu4.2), samba-common:amd64 (4.1.6+dfsg-1ubuntu2.14.04.1, 4.1.6+dfsg-1ubuntu2.14.04.2), gir1.2-webkit-3.0:amd64 (2.4.2-1ubuntu0.1, 2.4.3-1ubuntu2), linux-image-generic:amd64 (3.13.0.29.35, 3.13.0.30.36), libgphoto2-l10n:amd64 (2.5.3.1-1ubuntu2, 2.5.3.1-1ubuntu2.2), libsmbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.1, 4.1.6+dfsg-1ubuntu2.14.04.2)
End-Date: 2014-06-27  12:20:28
```

The kernel has been changed and some drivers. Before this update everything was working OK.

I'm also attaching the result of aplay -l (taken when everything was working)
```
[COLOR=#2E8B57][FONT=Monaco]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 0: Intel [HDA Intel], device 0: ALC1150 Analog [ALC1150 Analog][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 0: Intel [HDA Intel], device 1: ALC1150 Digital [ALC1150 Digital][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0[/FONT][/COLOR]
```

My motherboard is [http://www.msi.com/product/mb/Z97_GAMING_3.html#overview](http://www.msi.com/product/mb/Z97_GAMING_3.html#overview)

Do you have any idea how I could have working sound card back?

---

### Post by daniel10a on 2014-06-30
I've uninstalled [COLOR=#000000][FONT=Ubuntu Mono]oem-audio-hda-daily-dkms
[/FONT][/COLOR]Then I've installed it again and now it works[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

