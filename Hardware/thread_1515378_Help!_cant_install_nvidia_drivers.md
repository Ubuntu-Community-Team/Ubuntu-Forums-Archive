---
title: "Help! cant install nvidia drivers"
date: 2010-06-22
forum: Hardware
---

### Post by Thorntoon on 2010-06-22
Help! around 1/2 way through downloading nvidias 185 driver i got the error  **"SystemError: installArchives() failed" **
it happens every tim[B]e.
[/B]when i try jockey-text -l this happens 
jockey-text -l
Traceback (most recent call last):
  File "/usr/bin/jockey-text", line 130, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 380, in run
    self.list()
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 423, in list
    for h_id in self.backend().available(self.argv_options.mode):
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 185, in available
    return self.handlers.keys()
AttributeError: 'Backend' object has no attribute 'handlers'

Any help will be greatly appreciated ( if you cant already tell im a linux n00b :[ )

---

