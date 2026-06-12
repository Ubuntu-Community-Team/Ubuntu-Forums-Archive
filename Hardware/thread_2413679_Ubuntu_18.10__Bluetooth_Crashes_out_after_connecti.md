---
title: "Ubuntu 18.10 : Bluetooth Crashes out after connection."
date: 2019-02-28
forum: Hardware
---

### Post by neuman1812 on 2019-02-28
New install of Ubuntu 18.10.  Fully updated.  

When I connect my bluetooth speaker,  the moment I try and play any sound,  the bluetooth connection drops out.    


 My syslog during the event:

```
Feb 28 16:33:48 Bootes systemd[1]: Starting Load/Save RF Kill Switch Status...
Feb 28 16:33:48 Bootes systemd[1]: Started Load/Save RF Kill Switch Status.
Feb 28 16:33:53 Bootes snapd[2784]: udevmon.go:190: udev monitor observed remove event for unknown device "/sys/dentry(3669:systemd-rfkill.service)"
Feb 28 16:34:07 Bootes systemd[1]: Starting Load/Save RF Kill Switch Status...
Feb 28 16:34:07 Bootes systemd[1]: Started Load/Save RF Kill Switch Status.
Feb 28 16:34:12 Bootes snapd[2784]: udevmon.go:190: udev monitor observed remove event for unknown device "/sys/dentry(3715:systemd-rfkill.service)"
Feb 28 16:34:17 Bootes blueman-mechanism: Exiting 
Feb 28 16:34:24 Bootes kernel: [606047.910882] Bluetooth: hci0: command 0x0405 tx timeout
Feb 28 16:34:46 Bootes bluetoothd[31564]: connect error: Connection reset by peer (104)
Feb 28 16:34:46 Bootes blueman-applet[13130]: gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed
Feb 28 16:34:46 Bootes kernel: [606070.534560] input: A0:E9:DB:38:0A:AE as /devices/virtual/input/input16
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) config/udev: Adding input device A0:E9:DB:38:0A:AE (/dev/input/event9)
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) A0:E9:DB:38:0A:AE: Applying InputClass "libinput keyboard catchall"
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) Using input driver 'libinput' for 'A0:E9:DB:38:0A:AE'
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 64 paused 0
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) A0:E9:DB:38:0A:AE: always reports core events
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) Option "Device" "/dev/input/event9"
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) Option "_source" "server/udev"
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) event9  - A0:E9:DB:38:0A:AE: is tagged by udev as: Keyboard
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) event9  - A0:E9:DB:38:0A:AE: device is a keyboard
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) event9  - A0:E9:DB:38:0A:AE: device removed
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) Option "config_info" "udev:/sys/devices/virtual/input/input16/event9"
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) XINPUT: Adding extended input device "A0:E9:DB:38:0A:AE" (type: KEYBOARD, id 11)
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) Option "xkb_model" "pc105"
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) Option "xkb_layout" "us"
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (WW) Option "xkb_variant" requires a string value
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (WW) Option "xkb_options" requires a string value
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) event9  - A0:E9:DB:38:0A:AE: is tagged by udev as: Keyboard
Feb 28 16:34:46 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) event9  - A0:E9:DB:38:0A:AE: device is a keyboard
Feb 28 16:34:47 Bootes bluetoothd[31564]: /org/bluez/hci0/dev_A0_E9_DB_38_0A_AE/fd6: fd(37) ready
Feb 28 16:34:47 Bootes rtkit-daemon[1683]: Supervising 1 threads of 1 processes of 1 users.
Feb 28 16:34:47 Bootes rtkit-daemon[1683]: Successfully made thread 5058 of process 12875 (n/a) owned by '1000' RT at priority 5.
Feb 28 16:34:47 Bootes rtkit-daemon[1683]: Supervising 2 threads of 1 processes of 1 users.
Feb 28 16:34:47 Bootes gsd-media-keys[13078]: Unable to get default sink
Feb 28 16:34:47 Bootes gsd-media-keys[13078]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Feb 28 16:34:47 Bootes gsd-media-keys[13078]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Feb 28 16:34:48 Bootes gnome-shell[12852]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Feb 28 16:34:48 Bootes gnome-shell[12852]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Feb 28 16:35:01 Bootes bluetoothd[31564]: Start: Connection timed out (110)
Feb 28 16:35:01 Bootes pulseaudio[12875]: E: [bluetooth] bluez5-util.c: Transport Acquire() failed for transport /org/bluez/hci0/dev_A0_E9_DB_38_0A_AE/fd6 (Input/output error)
Feb 28 16:35:01 Bootes bluetoothd[31564]: avdtp_start failed
Feb 28 16:35:01 Bootes pulseaudio[12875]: E: [bluetooth] bluez5-util.c: Transport Acquire() failed for transport /org/bluez/hci0/dev_A0_E9_DB_38_0A_AE/fd6 (Operation Not Authorized)
Feb 28 16:35:03 Bootes bluetoothd[31564]: Abort: Connection timed out (110)
Feb 28 16:35:03 Bootes gsd-media-keys[13078]: Unable to get default sink
Feb 28 16:35:03 Bootes gsd-media-keys[13078]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Feb 28 16:35:03 Bootes gsd-media-keys[13078]: message repeated 3 times: [ gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed]
Feb 28 16:35:03 Bootes gnome-shell[12852]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Feb 28 16:35:03 Bootes gnome-shell[12852]: message repeated 3 times: [ gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed]
Feb 28 16:35:03 Bootes acpid: input device has been disconnected, fd 14
Feb 28 16:35:03 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) config/udev: removing device A0:E9:DB:38:0A:AE
Feb 28 16:35:03 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (**) Option "fd" "64"
Feb 28 16:35:03 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) event9  - A0:E9:DB:38:0A:AE: device removed
Feb 28 16:35:03 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) UnloadModule: "libinput"
Feb 28 16:35:03 Bootes /usr/lib/gdm3/gdm-x-session[12686]: (II) systemd-logind: releasing fd for 13:73
^C

```

---

