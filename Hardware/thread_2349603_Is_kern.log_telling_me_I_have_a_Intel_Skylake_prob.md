---
title: "Is kern.log telling me I have a Intel Skylake problem?"
date: 2017-01-16
forum: Hardware
---

### Post by Superdude_123 on 2017-01-16
After going through the kern.log files to see if I can narrow down what caused my system to just go down over night, I can see that I had an error in kern.log just before the system went back online:

Jan 15 23:52:48 CentralServer kernel: [ 34.568945] snd_hda_intel 0000:00:1f.3: azx_get_response timeout, switching to polling mode: last cmd=0x005a0000

I've also pulled out a section of my syslog file where I think things started to go south. I don't know what it means, but I'm wondering if it can be of any help:

```

Jan 15 23:55:27 CentralServer systemd[2359]: Reached target Timers.
Jan 15 23:55:27 CentralServer systemd[2359]: Reached target Sockets.
Jan 15 23:55:27 CentralServer systemd[2359]: Reached target Paths.
Jan 15 23:55:27 CentralServer systemd[2359]: Reached target Basic System.
Jan 15 23:55:27 CentralServer systemd[2359]: Reached target Default.
Jan 15 23:55:27 CentralServer systemd[2359]: Startup finished in 10ms.
Jan 15 23:55:27 CentralServer systemd[1]: Started User Manager for UID 1000.
Jan 15 23:55:41 CentralServer org.a11y.Bus[2488]: Activating service name='org.a11y.atspi.Registry'
Jan 15 23:55:41 CentralServer org.a11y.Bus[2488]: ** (process:2501): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Jan 15 23:55:41 CentralServer org.a11y.Bus[2488]: Successfully activated service 'org.a11y.atspi.Registry'
Jan 15 23:55:41 CentralServer org.a11y.atspi.Registry[2506]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jan 15 23:55:41 CentralServer gnome-session[2440]: gnome-session-is-accelerated: No composite extension.
Jan 15 23:55:41 CentralServer gnome-session[2440]: gnome-session-check-accelerated: Helper exited with code 256
Jan 15 23:55:46 CentralServer gnome-session[2440]: gnome-session-is-accelerated: No composite extension.
Jan 15 23:55:46 CentralServer gnome-session[2440]: gnome-session-check-accelerated: Helper exited with code 256
Jan 15 23:55:46 CentralServer gnome-session[2440]: gnome-session-binary[2440]: WARNING: software acceleration check failed: Child process exited with code 1
Jan 15 23:55:46 CentralServer gnome-session[2440]: gnome-session-binary[2440]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jan 15 23:55:46 CentralServer gnome-session-binary[2440]: WARNING: software acceleration check failed: Child process exited with code 1
Jan 15 23:55:46 CentralServer gnome-session-binary[2440]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jan 15 23:57:42 CentralServer systemd[1]: Stopping Manage, Install and Generate Color Profiles...
Jan 15 23:57:42 CentralServer systemd[1684]: Stopped target Default.
Jan 15 23:57:42 CentralServer systemd[1684]: Stopped target Basic System.
Jan 15 23:57:42 CentralServer systemd[1684]: Stopped target Paths.
Jan 15 23:57:42 CentralServer systemd[1684]: Reached target Shutdown.
Jan 15 23:57:42 CentralServer dbus[1131]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkitd.service'
Jan 15 23:57:42 CentralServer systemd[1]: Stopping User Manager for UID 108...
Jan 15 23:57:42 CentralServer systemd[1]: Stopping Daemon for power management...
Jan 15 23:57:42 CentralServer systemd[1]: Stopping Authenticate and Authorize Users to Run Privileged Tasks...
Jan 15 23:57:42 CentralServer systemd[1]: Stopped target Printer.
Jan 15 23:57:42 CentralServer systemd[1]: Stopping Session c1 of user lightdm.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped target Sound Card.
Jan 15 23:57:42 CentralServer systemd[1684]: Starting Exit the Session...
Jan 15 23:57:42 CentralServer systemd[1684]: Stopped target Sockets.
Jan 15 23:57:42 CentralServer systemd[1684]: Stopped target Timers.
Jan 15 23:57:42 CentralServer systemd[1]: Unmounting /raid5...
Jan 15 23:57:42 CentralServer systemd[1]: Stopping Session 2 of user squid.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped target Timers.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped Daily apt activities.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped Daily Cleanup of Temporary Directories.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped Timer to automatically refresh installed snaps.
Jan 15 23:57:42 CentralServer systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
Jan 15 23:57:42 CentralServer systemd[1]: Stopping User Manager for UID 1000...
Jan 15 23:57:42 CentralServer systemd[1]: Stopping Save/Restore Sound Card State...
Jan 15 23:57:42 CentralServer systemd[1]: Stopping RealtimeKit Scheduling Policy Service...
Jan 15 23:57:42 CentralServer systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped target Graphical Interface.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped target Multi-User System.
Jan 15 23:57:42 CentralServer systemd[1]: Stopped Initialize hardware monitoring sensors.
Jan 15 23:57:42 CentralServer rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1159" x-info="http://www.rsyslog.com"] exiting on signal 15. 
```

Could this have caused it? I've pulled all my /var/log files from the system, so if anything is needed, let me know and I can share.

---

