---
title: "scribes and fluxbox"
date: 2008-09-11
forum: General Help
---

### Post by savsav on 2008-09-11
scribes works perfectly in ubuntu.

But it will not launch when I use fluxbox.

Any ideas?

This is the output I get when I try to launch scribes from terminal:

sav@sav-desktop:~$ scribes
Traceback (most recent call last):
  File "/usr/bin/scribes", line 79, in <module>
    main(argv[1:])
  File "/usr/lib/python2.5/site-packages/SCRIBES/Main.py", line 48, in main
    __open()
  File "/usr/lib/python2.5/site-packages/SCRIBES/Main.py", line 59, in __open
    __open_via_dbus(uris)
  File "/usr/lib/python2.5/site-packages/SCRIBES/Main.py", line 77, in __open_via_dbus
    dbus_service = __get_dbus_service()
  File "/usr/lib/python2.5/site-packages/SCRIBES/Main.py", line 121, in __get_dbus_service
    from info import dbus_iface, session_bus
  File "/usr/lib/python2.5/site-packages/SCRIBES/info.py", line 32, in <module>
    session_bus = SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-L5vfKIe3Rt: Connection refused

---

### Post by savsav on 2008-09-11
I just tried sudo scribes

and it launches.

What could be causing this?

---

