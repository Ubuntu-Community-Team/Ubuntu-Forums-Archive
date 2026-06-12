---
title: "[SOLVED] Hardware Drivers (jockey-gtk) not working in Intrepid Ibex"
date: 2008-11-05
forum: General Help
---

### Post by Altay_H on 2008-11-05
Since I upgraded to Intrepid Ibex I have been unable to use Hardware Drivers. It lists the available drivers correctly, but simply gives a blank error or no error at all after a while when trying to install one. Running it in the terminal gives the following error:

```

:~$ jockey-gtk -e xorg:fglrx
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 377, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 395, in run
    self.argv_options.confirm, False):
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 594, in set_handler_enable
    polkit_auth_wrapper(self.backend().set_enabled, handler_id, enable)
  File "/usr/lib/python2.5/site-packages/jockey/backend.py", line 117, in polkit_auth_wrapper
    return fn(*args, **kwargs)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

:~$ jockey-gtk -c
ERROR:dbus.proxies:Introspect error on :1.33:/DeviceDriver: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Any ideas what might be wrong?

---

### Post by Altay_H on 2008-11-05
Updating my packages solved my problem. If anyone else is having the same problem, just run:

```
sudo apt-get update
```

---

