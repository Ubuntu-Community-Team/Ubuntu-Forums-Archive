---
title: "Cannot get external screen to work on ubuntu 16 or 18"
date: 2018-09-20
forum: Hardware
---

### Post by eriklot on 2018-09-20
Hi. I have a Dell Precision 7530 with a Radeon Pro WX 4150 GPU, and I cannot get the computer to work when external screen(s) are connected. I have tried live booting into Ubuntu 16.04 and Ubuntu 18.04, and I have also installed Ubuntu 18.04 (dual boot alongside windows 10), all with the same behavior. The behavior is as follows:
[LIST=1]
[*]I plug in one or more screens into the laptop, HDMI and Display port
[*]Turn on the computer
[*]It fails somewhere in the boot process.
[LIST=1]
[*]In Ubuntu 18.04 live boot it prints "Starting user manager for UID 121" and then "Stopping User Manager...", and finally "Removed slice User Slice of ubuntu"
[*]In Ubuntu 16.04 live boot it gets to the login screen (which it bypasses when no screens are connected). When I click to login, it waits a short while and displays the login screen again.
[/LIST]
[/LIST]
Or:
[LIST=1]
[*]I disconnect all external screens
[*]Turn on the computer
[*]Everything seems to work fine
[*]Plug in one or two screens
[*]The screens are not detected, and not visible in devices section under settings.
[/LIST]

Live booting into Ubuntu 18.04, I have logged into the command line using Ctrl+Alt+F2, and then read /var/log/syslog. In there I found the following which i suspect is relevant: 

```

[COLOR=#000000]Sep 20 05:20:45 ubuntu kernel: [   56.915289] [drm] {2560x1440, 2720x1481@241500Khz}[/COLOR]Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE)
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) Backtrace:
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) 0: /usr/lib/xorg/Xorg (xorg_backtrace+0x4d) [0x55f8210348ad]
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) 1: /usr/lib/xorg/Xorg (0x55f820e7c000+0x1bc649) [0x55f821038649]
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f293b682000+0x12890) [0x7f293b694890]
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE)
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) Segmentation fault at address 0x0
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE)
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: Fatal server error:
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) Caught signal 11 (Segmentation fault). Server aborting
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE)
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE)
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: Please consult the The X.Org Foundation support
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: #011 at http://wiki.x.org
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]:  for help.
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) Please also check the log file at "/var/lib/gdm3/.local/share/xorg/Xorg.0.log" for additional information.
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE)
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (II) AIGLX: Suspending AIGLX clients for VT switch
Sep 20 05:20:45 ubuntu /usr/lib/gdm3/gdm-x-session[3254]: (EE) Server terminated with error (1). Closing log file.
Sep 20 05:20:45 ubuntu systemd[1]: Reloading.
Sep 20 05:20:45 ubuntu dhclient[2013]: DHCPDISCOVER on eno1 to 255.255.255.255 port 67 interval 14 (xid=0x44244f47)
Sep 20 05:20:45 ubuntu systemd[1]: Mounting Mount unit for gnome-characters, revision 103...
Sep 20 05:20:45 ubuntu systemd[1]: Mounted Mount unit for gnome-characters, revision 103.
Sep 20 05:20:45 ubuntu kernel: [   56.921707] [drm] HBRx4 pass VS=1, PE=1
Sep 20 05:20:45 ubuntu kernel: [   57.214686] audit: type=1400 audit(1537420845.628:60): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.gnome-characters" pid=3504 comm="apparmor_parser"
Sep 20 05:20:45 ubuntu kernel: [   57.262714] audit: type=1400 audit(1537420845.676:61): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=3506 comm="apparmor_parser"
Sep 20 05:20:46 ubuntu at-spi-bus-launcher[3330]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Sep 20 05:20:46 ubuntu at-spi-bus-launcher[3330]:       after 21 requests (21 known processed) with 0 events remaining.
Sep 20 05:20:46 ubuntu kernel: [   57.700461] [drm] {2560x1440, 2720x1481@241500Khz}
Sep 20 05:20:46 ubuntu kernel: [   57.700508] [drm] {2560x1440, 2720x1481@241500Khz}
Sep 20 05:20:46 ubuntu org.gnome.Shell.desktop[3346]: Window manager warning: Configuring CRTC 64 with mode 102 (2560 x 1440 @ 59.950550) at position 6400, 0 and transform 0 failed
Sep 20 05:20:46 ubuntu org.gnome.Shell.desktop[3346]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Sep 20 05:20:46 ubuntu org.gnome.Shell.desktop[3346]:       after 470 requests (467 known processed) with 2 events remaining.
Sep 20 05:20:46 ubuntu gnome-session[3328]: gnome-session-binary[3328]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Sep 20 05:20:46 ubuntu gnome-session-binary[3328]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Sep 20 05:20:46 ubuntu gnome-shell[3573]: Failed to create backend: Unable to open display ':0'
Sep 20 05:20:46 ubuntu gnome-session[3328]: gnome-session-binary[3328]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Sep 20 05:20:46 ubuntu gnome-session[3328]: gnome-session-binary[3328]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Sep 20 05:20:46 ubuntu gnome-session-binary[3328]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Sep 20 05:20:46 ubuntu gnome-session-binary[3328]: Unrecoverable failure in required component org.gnome.Shell.desktop
Sep 20 05:20:46 ubuntu gnome-session[3328]: gnome-session-binary[3328]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Sep 20 05:20:46 ubuntu gnome-session-binary[3328]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Sep 20 05:20:46 ubuntu gnome-session-binary[3328]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Sep 20 05:20:46 ubuntu gdm3: GdmDisplay: display lasted 2.713625 seconds [COLOR=#000000]Sep 20 05:20:46 ubuntu gdm3: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
[/COLOR]
```

The segfault hints at the log file [COLOR=#000000]/var/lib/gdm3/.local/share/xorg/Xorg.0.log, which at the very bottom says that it received a segmentation fault. This file also shows that it has detected both my screens (BenQ and Dell) correctly.

I have also run all of Dells update tools from windows 10, including updating BIOS. 

Any help is greatly appreciated.


[/COLOR]

---

### Post by eriklot on 2018-09-21
It turns out that this problem was caused by a setting in bios! Under video -> Switchable graphics, switchable graphics was enabled. The description says that it is only supported on windows 7 and higher and ubuntu. This was odd though, as it worked for neither ubuntu 18.04 nor 16.04! **Disabling it fixed my problem.**

---

