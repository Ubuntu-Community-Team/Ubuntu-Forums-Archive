---
title: "Ubuntu 8.04 freeze"
date: 2008-11-17
forum: General Help
---

### Post by juny20 on 2008-11-17
Hi everyone,
I am hoping that someone can tell me how to read the syslog or see if there are any problems there. My system froze three times for no reason. I did a fresh install of 8.04 as 8.10 was giving me too many problems. The system was working perfectly fine and then wham! It would not move at all. I had to do a hard reboot. This is the section of the syslog right before the last freeze last night:

Nov 16 21:17:39 juny20-desktop gdmgreeter[5967]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Nov 16 21:17:39 juny20-desktop gdmgreeter[5967]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Nov 16 21:17:39 juny20-desktop gdmgreeter[5967]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Nov 16 21:17:39 juny20-desktop gdmgreeter[5967]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Nov 16 21:17:46 juny20-desktop kernel: [  109.801686] eth0: no IPv6 routers present
Nov 16 21:25:38 juny20-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 16 21:25:38 juny20-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 16 21:37:25 juny20-desktop -- MARK --
Nov 16 21:57:25 juny20-desktop -- MARK --
Nov 16 22:17:01 juny20-desktop /USR/SBIN/CRON[6547]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 16 22:37:25 juny20-desktop -- MARK --
Nov 16 22:57:25 juny20-desktop -- MARK --
Nov 16 23:04:16 juny20-desktop init: tty4 main process (4925) killed by TERM signal
Nov 16 23:04:16 juny20-desktop init: tty5 main process (4926) killed by TERM signal
Nov 16 23:04:16 juny20-desktop init: tty2 main process (4930) killed by TERM signal
Nov 16 23:04:16 juny20-desktop init: tty3 main process (4931) killed by TERM signal
Nov 16 23:04:16 juny20-desktop init: tty6 main process (4935) killed by TERM signal
Nov 16 23:04:16 juny20-desktop init: tty1 main process (5896) killed by TERM signal
Nov 16 23:04:27 juny20-desktop avahi-daemon[5355]: Got SIGTERM, quitting.
Nov 16 23:04:27 juny20-desktop avahi-daemon[5355]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.103.
Nov 17 18:26:15 juny20-desktop syslogd 1.5.0#1ubuntu1: restart.


By the way, I have a wired Ethernet network connection. If anyone can provide any insights into this it'll be much appreciated.
Thanks!!!

---

### Post by juny20 on 2008-11-17
It happened again!!!! Here is the data from syslog:

Nov 17 20:33:44 juny20-desktop kernel: [ 7694.611288] sd 4:0:0:0: [sdc] 494080 512-byte hardware sectors (253 MB)
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.616290] sd 4:0:0:0: [sdc] Write Protect is off
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.616299] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.616302] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.621282] sd 4:0:0:0: [sdc] 494080 512-byte hardware sectors (253 MB)
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.626287] sd 4:0:0:0: [sdc] Write Protect is off
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.626296] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.626299] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Nov 17 20:33:44 juny20-desktop kernel: [ 7694.626309]  sdc: sdc1
Nov 17 20:33:44 juny20-desktop NetworkManager: <debug> [1226975624.694697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6563_3939'). 
Nov 17 20:33:44 juny20-desktop hald: mounted /dev/sdc1 on behalf of uid 1000
Nov 17 20:33:53 juny20-desktop kernel: [ 7703.552387] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd f-spot rqt 128 rq 6 len 1000 ret -110
Nov 17 20:33:54 juny20-desktop kernel: [ 7704.570667] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd f-spot rqt 128 rq 6 len 1000 ret -110
Nov 17 20:46:13 juny20-desktop -- MARK --
Nov 17 20:51:54 juny20-desktop hald: unmounted /dev/sdc1 from '/media/disk' on behalf of uid 0
Nov 17 20:51:54 juny20-desktop NetworkManager: <debug> [1226976714.148989] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6563_3939'). 
Nov 17 21:06:14 juny20-desktop -- MARK --
Nov 17 21:17:01 juny20-desktop /USR/SBIN/CRON[9610]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 17 21:36:53 juny20-desktop syslogd 1.5.0#1ubuntu1: restart.

I don't know why the system keeps freezing! It works flawlessly and then boom! It freezes.

---

