---
title: "'session != NULL' failed (Log-in screen is looping for ever)"
date: 2018-01-18
forum: Hardware
---

### Post by wrongusername2 on 2018-01-18
Hi,

Ubuntu 16,04 Log-in screen is looping. I have attached the Sys.log.
-Native NVidia Driver
-VirtualBox(down loaded from S/w repo)

Please go through the log and let me know what is wrong. [B]
    session_get_login1_session_id: assertion 'session != NULL' failed[/B]
   [B]  gnome-session-binary[5434]: CRITICAL: We failed, but the fail whale is dead. Sorry....
[/B]
Three days ago I had same issue, and I solved it by re-imaging the OS using DD. On both the occasions this happened after installing VirtualBOX. 

```

Jan 18 18:00:04 afterwindowsZBook lightdm[1129]: message repeated 4 times: [ /etc/modprobe.d is not a file]
Jan 18 18:00:04 afterwindowsZBook lightdm[1129]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Jan 18 18:00:04 afterwindowsZBook systemd[1]: Started Session c9 of user lightdm.
Jan 18 18:00:04 afterwindowsZBook org.a11y.atspi.Registry[4119]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jan 18 18:00:08 afterwindowsZBook org.freedesktop.Notifications[4111]: Xlib:  extension "GLX" missing on display ":0".
Jan 18 18:00:08 afterwindowsZBook org.freedesktop.Notifications[4111]: ** (notify-osd:4228): WARNING **: dnd_is_idle_inhibited(): got error "No such method 'IsInhibited'"
Jan 18 18:00:24 afterwindowsZBook pulseaudio[3226]: [pulseaudio] module.c: After module unload, module 'module-null-sink' was still loaded!
Jan 18 18:00:24 afterwindowsZBook systemd[1]: Stopping User Manager for UID 1000...


Jan 18 18:03:11 afterwindowsZBook systemd[1]: Started Network Manager Script Dispatcher Service.
Jan 18 18:03:11 afterwindowsZBook nm-dispatcher: req:1 'up' [wlo1]: new request (1 scripts)
Jan 18 18:03:11 afterwindowsZBook nm-dispatcher: req:1 'up' [wlo1]: start running ordered scripts...
Jan 18 18:03:11 afterwindowsZBook whoopsie[1284]: [18:03:11] online
Jan 18 18:03:11 afterwindowsZBook avahi-daemon[946]: Joining mDNS multicast group on interface wlo1.IPv6 with address fe80::cd5e:2e4:5f4a:3d25.
Jan 18 18:03:11 afterwindowsZBook avahi-daemon[946]: New relevant interface wlo1.IPv6 for mDNS.
Jan 18 18:03:11 afterwindowsZBook avahi-daemon[946]: Registering new address record for fe80::cd5e:2e4:5f4a:3d25 on wlo1.*.
Jan 18 18:03:12 afterwindowsZBook org.a11y.atspi.Registry[5441]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jan 18 18:03:12 afterwindowsZBook gnome-session[5434]: Xlib:  extension "GLX" missing on display ":0".
Jan 18 18:03:12 afterwindowsZBook gnome-session[5434]: message repeated 3 times: [ Xlib:  extension "GLX" missing on display ":0".]
Jan 18 18:03:12 afterwindowsZBook gnome-session[5434]: gnome-session-is-accelerated: No hardware 3D support.
Jan 18 18:03:12 afterwindowsZBook gnome-session[5434]: Xlib:  extension "GLX" missing on display ":0".
Jan 18 18:03:12 afterwindowsZBook gnome-session[5434]: gnome-session-check-accelerated: Helper exited with code 256
Jan 18 18:03:12 afterwindowsZBook gnome-session[5434]: gnome-session-binary[5434]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jan 18 18:03:12 afterwindowsZBook gnome-session-binary[5434]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jan 18 18:03:12 afterwindowsZBook rtkit-daemon[1343]: Successfully made thread 5532 of process 5532 (n/a) owned by '1000' high priority at nice level -11.

```

Thanks

---

