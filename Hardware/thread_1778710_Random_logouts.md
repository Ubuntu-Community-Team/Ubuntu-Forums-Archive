---
title: "Random logouts"
date: 2011-06-09
forum: Hardware
---

### Post by cmavr8 on 2011-06-09
I get logged-out of my session at random times, even when I'm not working on the computer. Ubuntu 11.04 on a Thinkpad X201s.

The syslog is full of errors, and I cannot determine which one is responsible. Can you help?

I think the logout occured after 17:10:26
```

Jun  9 17:10:13 PC crontab[12313]: (root) LIST (root)
Jun  9 17:10:26 PC kernel: [23673.061919] pidgin[3097] general protection ip:7fb8e79568b5 sp:7fffcbf8a680 error:0 in libc-2.13.so[7fb8e791d000+18a000]
Jun  9 17:10:27 PC kernel: [23673.396481] workrave[1719]: segfault at 175849c0 ip 00007f6b3c29a8b5 sp 00007f6b34155b50 error 4 in libc-2.13.so[7f6b3c261000+18a000]
Jun  9 17:10:27 PC NetworkManager[819]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
Jun  9 17:10:27 PC NetworkManager[819]: <info> (wlan0): deactivating device (reason: 38).
Jun  9 17:10:27 PC NetworkManager[819]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3978
Jun  9 17:10:27 PC avahi-daemon[821]: Withdrawing address record for 192.168.1.226 on wlan0.
Jun  9 17:10:27 PC avahi-daemon[821]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.226.
Jun  9 17:10:27 PC avahi-daemon[821]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun  9 17:10:27 PC kernel: [23674.158771] wlan0: deauthenticating from 00:40:77:bb:55:12 by local choice (reason=3)
Jun  9 17:10:27 PC vmnetBridge: Removing interface wlan0 index:3
Jun  9 17:10:27 PC kernel: [23674.296002] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun  9 17:10:27 PC kernel: [23674.296012] cfg80211: Restoring regulatory settings
Jun  9 17:10:27 PC kernel: [23674.296019] cfg80211: Calling CRDA to update world regulatory domain
Jun  9 17:10:28 PC kernel: [23674.356364] bridge-wlan0: disabling the bridge
Jun  9 17:10:28 PC wpa_supplicant[1123]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  9 17:10:28 PC vmnetBridge: Stopped bridge wlan0 to virtual network 0.
Jun  9 17:10:28 PC vmnetBridge: Adding interface wlan0 index:3
Jun  9 17:10:28 PC kernel: [23674.405843] bridge-wlan0: down
Jun  9 17:10:28 PC kernel: [23674.405852] bridge-wlan0: detached
Jun  9 17:10:28 PC vmnetBridge: Started bridge wlan0 to virtual network 0.
Jun  9 17:10:28 PC kernel: [23674.446360] /dev/vmnet: open called by PID 1311 (vmnet-bridge)
Jun  9 17:10:28 PC kernel: [23674.446378] /dev/vmnet: hub 0 does not exist, allocating memory.
Jun  9 17:10:28 PC kernel: [23674.446409] /dev/vmnet: port on hub 0 successfully opened
Jun  9 17:10:28 PC kernel: [23674.446429] bridge-wlan0: device is wireless, enabling SMAC
Jun  9 17:10:28 PC kernel: [23674.446435] bridge-wlan0: up
Jun  9 17:10:28 PC kernel: [23674.446442] bridge-wlan0: attached
Jun  9 17:10:28 PC kernel: [23674.661645] bonobo-activati[4874] trap divide error ip:7f46934dd0f2 sp:7f46918062a0 error:0 in libglib-2.0.so.0.2800.7[7f46934ab000+116000]
Jun  9 17:10:28 PC kernel: [23674.848354] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun  9 17:10:28 PC kernel: [23674.848365] cfg80211: World regulatory domain updated:
Jun  9 17:10:28 PC kernel: [23674.848367] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  9 17:10:28 PC kernel: [23674.848372] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  9 17:10:28 PC kernel: [23674.848376] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  9 17:10:28 PC kernel: [23674.848380] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  9 17:10:28 PC kernel: [23674.848383] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  9 17:10:28 PC kernel: [23674.848387] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  9 17:10:29 PC pulseaudio[12402]: pid.c: Stale PID file, overwriting.
Jun  9 17:10:29 PC pulseaudio[12402]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
Jun  9 17:10:29 PC pulseaudio[12402]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-KHGG39ZweS: Connection refused
Jun  9 17:10:30 PC pulseaudio[12407]: pid.c: Daemon already running.
Jun  9 17:10:30 PC pulseaudio[12409]: pid.c: Daemon already running.
Jun  9 17:10:30 PC pulseaudio[12412]: pid.c: Daemon already running.
Jun  9 17:10:30 PC pulseaudio[12413]: pid.c: Daemon already running.
Jun  9 17:10:30 PC pulseaudio[12414]: pid.c: Daemon already running.
Jun  9 17:10:30 PC acpid: client 955[0:0] has disconnected
Jun  9 17:10:30 PC acpid: client connected from 12410[0:0]
Jun  9 17:10:30 PC acpid: 1 client rule loaded
Jun  9 17:10:32 PC rtkit-daemon[1383]: Successfully made thread 12460 of process 12460 (n/a) owned by '113' high priority at nice level -11.
Jun  9 17:10:32 PC rtkit-daemon[1383]: Supervising 1 threads of 1 processes of 2 users.
Jun  9 17:10:32 PC rtkit-daemon[1383]: Successfully made thread 12479 of process 12460 (n/a) owned by '113' RT at priority 5.
Jun  9 17:10:32 PC rtkit-daemon[1383]: Supervising 2 threads of 1 processes of 2 users.
Jun  9 17:10:32 PC rtkit-daemon[1383]: Successfully made thread 12498 of process 12460 (n/a) owned by '113' RT at priority 5.
Jun  9 17:10:32 PC rtkit-daemon[1383]: Supervising 3 threads of 1 processes of 2 users.
Jun  9 17:10:32 PC pulseaudio[12460]: module-alsa-card.c: Failed to find a working profile.
Jun  9 17:10:32 PC pulseaudio[12460]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jun  9 17:10:32 PC anacron[12508]: Anacron 2.3 started on 2011-06-09
Jun  9 17:10:32 PC anacron[12508]: Normal exit (0 jobs run)
Jun  9 17:10:33 PC kernel: [23680.189154] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Jun  9 17:10:33 PC gdm-simple-greeter[12450]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jun  9 17:10:33 PC kernel: [23680.209495] EXT4-fs (sda3): re-mounted. Opts: commit=0
Jun  9 17:10:34 PC gdm-session-worker[12458]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun  9 17:11:09 PC vmnetBridge: Removing interface wlan0 index:3
Jun  9 17:11:09 PC kernel: [23715.998545] bridge-wlan0: disabling the bridge
Jun  9 17:11:09 PC vmnetBridge: Stopped bridge wlan0 to virtual network 0.
Jun  9 17:11:09 PC kernel: [23716.048212] bridge-wlan0: down
Jun  9 17:11:09 PC kernel: [23716.048225] bridge-wlan0: detached
```

---

### Post by wolfen69 on 2011-06-09
Have you done Memtest? That was happening to me until I bought new memory.

---

### Post by mykrob on 2011-06-09
lots of people are having the random logout issue. A possible fix was released yesterday. Open the update manager and enable natty-proposed, then refresh and run updates and see what happens.

i've drained my battery three times today and not had a single logout, so i hope its fixed...

---

### Post by cmavr8 on 2011-06-10
Memtest showed nothing...

Update done, let's see... thanks

---

### Post by cmavr8 on 2011-06-17
> **cmavr8 said:**
> Memtest showed nothing...

Update done, let's see... thanks

Logouts continue!
Here's a new log that starts from the moment the logout was triggered, and ends when it was completed.

I think Network Manager does it... what do you think?

> Jun 17 13:38:43 PC NetworkManager[586]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
Jun 17 13:38:43 PC NetworkManager[586]: <info> (wlan0): deactivating device (reason: 38).
Jun 17 13:38:43 PC acpid: client 2978[0:0] has disconnected
Jun 17 13:38:43 PC acpid: client connected from 6198[0:0]
Jun 17 13:38:43 PC acpid: 1 client rule loaded
Jun 17 13:38:44 PC NetworkManager[586]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3484
Jun 17 13:38:44 PC kernel: [91988.329071] wlan0: deauthenticating from 00:40:77:bb:55:12 by local choice (reason=3)
Jun 17 13:38:44 PC kernel: [91988.521386] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 17 13:38:44 PC kernel: [91988.521395] cfg80211: Restoring regulatory settings
Jun 17 13:38:44 PC kernel: [91988.521405] cfg80211: Calling CRDA to update world regulatory domain
Jun 17 13:38:44 PC kernel: [91988.526251] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun 17 13:38:44 PC kernel: [91988.526261] cfg80211: World regulatory domain updated:
Jun 17 13:38:44 PC kernel: [91988.526264] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 17 13:38:44 PC kernel: [91988.526269] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 17 13:38:44 PC kernel: [91988.526273] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 17 13:38:44 PC kernel: [91988.526277] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 17 13:38:44 PC kernel: [91988.526282] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 17 13:38:44 PC kernel: [91988.526286] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 17 13:38:44 PC vmnetBridge: Removing interface wlan0 index:3
Jun 17 13:38:44 PC wpa_supplicant[900]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 17 13:38:44 PC avahi-daemon[585]: Withdrawing address record for 192.168.1.226 on wlan0.
Jun 17 13:38:44 PC avahi-daemon[585]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.226.
Jun 17 13:38:44 PC avahi-daemon[585]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 17 13:38:44 PC kernel: [91988.592598] bridge-wlan0: disabling the bridge
Jun 17 13:38:44 PC vmnetBridge: Stopped bridge wlan0 to virtual network 0.
Jun 17 13:38:44 PC vmnetBridge: Adding interface wlan0 index:3
Jun 17 13:38:44 PC vmnetBridge: Started bridge wlan0 to virtual network 0.
Jun 17 13:38:44 PC kernel: [91988.651194] bridge-wlan0: down
Jun 17 13:38:44 PC kernel: [91988.651204] bridge-wlan0: detached
Jun 17 13:38:44 PC kernel: [91988.651288] /dev/vmnet: open called by PID 1331 (vmnet-bridge)
Jun 17 13:38:44 PC kernel: [91988.651304] /dev/vmnet: hub 0 does not exist, allocating memory.
Jun 17 13:38:44 PC kernel: [91988.651343] /dev/vmnet: port on hub 0 successfully opened
Jun 17 13:38:44 PC kernel: [91988.651358] bridge-wlan0: device is wireless, enabling SMAC
Jun 17 13:38:44 PC kernel: [91988.651364] bridge-wlan0: up
Jun 17 13:38:44 PC kernel: [91988.651370] bridge-wlan0: attached
Jun 17 13:38:45 PC rtkit-daemon[1466]: Successfully made thread 6270 of process 6270 (n/a) owned by '113' high priority at nice level -11.
Jun 17 13:38:45 PC rtkit-daemon[1466]: Supervising 1 threads of 1 processes of 1 users.
Jun 17 13:38:45 PC rtkit-daemon[1466]: Successfully made thread 6271 of process 6270 (n/a) owned by '113' RT at priority 5.
Jun 17 13:38:45 PC rtkit-daemon[1466]: Supervising 2 threads of 1 processes of 1 users.
Jun 17 13:38:45 PC rtkit-daemon[1466]: Successfully made thread 6272 of process 6270 (n/a) owned by '113' RT at priority 5.
Jun 17 13:38:45 PC rtkit-daemon[1466]: Supervising 3 threads of 1 processes of 1 users.
Jun 17 13:38:45 PC pulseaudio[6270]: module-alsa-card.c: Failed to find a working profile.
Jun 17 13:38:45 PC pulseaudio[6270]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jun 17 13:38:45 PC gdm-simple-greeter[6261]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jun 17 13:38:45 PC gdm-session-worker[6264]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed


---

