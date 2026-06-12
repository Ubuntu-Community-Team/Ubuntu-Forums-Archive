---
title: "Ubuntu crashes"
date: 2009-04-13
forum: Hardware
---

### Post by orawax on 2009-04-13
Ubuntu has crashed (exited) already twice today.

Here's the relevant info from /var/log/syslog:

First crash

```
Apr 13 15:52:11 laptop init: tty4 main process (4293) killed by TERM signal
Apr 13 15:52:12 laptop init: tty5 main process (4294) killed by TERM signal
Apr 13 15:52:12 laptop init: tty2 main process (4301) killed by TERM signal
Apr 13 15:52:12 laptop init: tty3 main process (4302) killed by TERM signal
Apr 13 15:52:12 laptop init: tty6 main process (4303) killed by TERM signal
Apr 13 15:52:12 laptop init: tty1 main process (5410) killed by TERM signal
Apr 13 15:52:13 laptop console-kit-daemon[4830]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)' 
Apr 13 15:52:13 laptop console-kit-daemon[4830]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Apr 13 15:52:13 laptop console-kit-daemon[4830]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Apr 13 15:52:14 laptop bonobo-activation-server (user-14432): could not associate with desktop session: Failed to connect to socket /tmp/dbus-rt6rIOpwxI: Connection refused
Apr 13 15:52:15 laptop acpid: client has disconnected 
Apr 13 15:52:21 laptop bluetoothd[5132]: bridge pan0 removed
Apr 13 15:52:21 laptop bluetoothd[5132]: Stopping SDP server
Apr 13 15:52:21 laptop bluetoothd[5132]: Exit
Apr 13 15:52:21 laptop avahi-daemon[4705]: Got SIGTERM, quitting.
Apr 13 15:52:21 laptop avahi-daemon[4705]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.105.
Apr 13 15:52:22 laptop exiting on signal 15
```

Second crash

```
Apr 13 16:33:53 laptop init: tty4 main process (4337) killed by TERM signal
Apr 13 16:33:53 laptop init: tty5 main process (4338) killed by TERM signal
Apr 13 16:33:53 laptop init: tty2 main process (4345) killed by TERM signal
Apr 13 16:33:53 laptop init: tty3 main process (4346) killed by TERM signal
Apr 13 16:33:53 laptop init: tty6 main process (4347) killed by TERM signal
Apr 13 16:33:53 laptop init: tty1 main process (5463) killed by TERM signal
Apr 13 16:33:54 laptop pidgin: *** glibc detected *** pidgin: munmap_chunk(): invalid pointer: 0x0a35d310 *** 
Apr 13 16:33:54 laptop bonobo-activation-server (user-12698): could not associate with desktop session: Failed to connect to socket /tmp/dbus-D74WFE0o6o: Connection refused
Apr 13 16:33:55 laptop console-kit-daemon[4874]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `<invalid>' 
Apr 13 16:33:55 laptop console-kit-daemon[4874]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Apr 13 16:33:55 laptop console-kit-daemon[4874]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Apr 13 16:33:57 laptop acpid: client has disconnected 
Apr 13 16:34:00 laptop bluetoothd[5183]: bridge pan0 removed
Apr 13 16:34:00 laptop bluetoothd[5183]: Stopping SDP server
Apr 13 16:34:00 laptop bluetoothd[5183]: Exit
Apr 13 16:34:00 laptop avahi-daemon[4749]: Got SIGTERM, quitting.
Apr 13 16:34:00 laptop avahi-daemon[4749]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.105.
Apr 13 16:34:01 laptop exiting on signal 15
```

What is this?

---

### Post by q.dinar on 2010-10-28
i have come home and see white ubuntu logo on black background, keyboard and mouse does not work. then i have restarted. (i should try ctrl+alt+f1 etc) then i have seen in syslog:
```
Oct 28 19:49:36 dinar-desktop init: tty4 main process (1668) killed by TERM signal
Oct 28 19:49:36 dinar-desktop init: tty5 main process (1670) killed by TERM signal
Oct 28 19:49:36 dinar-desktop init: cron main process (1718) killed by TERM signal
Oct 28 19:49:36 dinar-desktop init: tty2 main process (1681) killed by TERM signal
Oct 28 19:49:36 dinar-desktop init: tty3 main process (1683) killed by TERM signal
Oct 28 19:49:36 dinar-desktop init: tty6 main process (1687) killed by TERM signal
Oct 28 19:49:36 dinar-desktop init: tty1 main process (4173) killed by TERM signal
Oct 28 19:49:36 dinar-desktop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
Oct 28 19:49:36 dinar-desktop acpid: exiting
Oct 28 19:49:37 dinar-desktop kernel: Kernel logging (proc) stopped.
```

---

