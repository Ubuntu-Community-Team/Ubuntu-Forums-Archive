---
title: "xsession error"
date: 2008-07-26
forum: General Help
---

### Post by jj2323us on 2008-07-26
To make a long story short, this newbie did something dumb involving nautilus, sudo, and permissions.  I have managed to get rid of my "gdm could not write to your authorization file" errors, but I am still getting xsession errors that will not let me log in.  Below is the .xsession-errors file, but I'm afraid I can't make any sense of it.  Any help would be appreciated.
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(seahorse-agent:6208): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.

(process:6208): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.

(gconf-sanity-check-2:6262): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.
SESSION_MANAGER=local/jason-ubuntu:/tmp/.ICE-unix/6208
Could not get password database information for UID of current process: User "???" unknown or no memory to allocate password entry

Failed to start message bus: Memory allocation failure in message bus
dbus-daemon exited unexpectedly
**
** ERROR:(gsm-dbus.c:118):gsm_dbus_daemon_start: assertion failed: (dbus_daemon_pid != 0)
```

---

