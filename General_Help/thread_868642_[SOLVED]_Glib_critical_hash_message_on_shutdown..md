---
title: "[SOLVED] Glib critical hash message on shutdown."
date: 2008-07-24
forum: General Help
---

### Post by Kevbert on 2008-07-24
I'm using Hardy 8.0.4.1 on an AMD64 PC via nVidia graphics, Broadcom 4306 wireless.  When I shutdown my PC I get a Glib critical error and something about hash, but the error is only displayed for a short time.
Which log would this be saved in ?  I've looked in the /var directory and can't see the error in the log files.

---

### Post by ajmorris on 2008-07-24
> **Kevbert said:**
> I'm using Hardy 8.0.4.1 on an AMD64 PC via nVidia graphics, Broadcom 4306 wireless. When I shutdown my PC I get a Glib critical error and something about hash, but the error is only displayed for a short time.
Which log would this be saved in ? I've looked in the /var directory and can't see the error in the log files.
 
Things in the shutdown runlevel should be stored in /var/log/syslog. Being on an AMD64 however, it may differ, you might like to look in /var/log/messages as well. It should be in one of those.
 
AJ

---

### Post by Kevbert on 2008-07-24
Thanks ajmorris.  I've found the bug is syslog.0.  The error has been already reported on [[COLOR="Red"]launchpad[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/249039/").  I've just added a note.
Here's part of the log:
```
Jul 23 21:02:40 kevin-dt1b init: tty1 main process (6471) killed by TERM signal
Jul 23 21:02:40 kevin-dt1b gdm[6258]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 23 21:02:40 kevin-dt1b gdm[6258]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Jul 23 21:02:40 kevin-dt1b avahi-daemon[5490]: Got SIGTERM, quitting.
```
It seems to have no effect on the system at present...

---

### Post by Kevbert on 2008-07-25
Closed as awaiting output from Launchpad - this may take a while.

---

