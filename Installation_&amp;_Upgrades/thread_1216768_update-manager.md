---
title: "update-manager"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by cccc on 2009-07-18
hi

I've done the Upgrade to Ubuntu Karmic, but **update-manager** shows these errors:```

# LANG=C update-manager --devel-release
warning: could not initiate dbus
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:36: RuntimeWarning: missing handler 'on_button_fetch_cancel_clicked'
  self.builder.connect_signals(self)
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:36: RuntimeWarning: missing handler 'on_expander_details_activate'
  self.builder.connect_signals(self)
Error setting launch_time:  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 99, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 192, in __init__
    self.restore_state()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 685, in restore_state
    expanded = self.gconfclient.get_bool("/apps/update-manager/show_details")
glib.GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```
Howto solve these all problems?

---

### Post by deputycleric on 2012-01-02
Hmm, I'm getting a very similar error in Natty:

warning: could not initiate dbus
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 107, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 283, in __init__
    self.install_backend = backend.get_backend(self.window_main)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/backend/__init__.py", line 49, in get_backend
    return InstallBackendAptdaemon(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 21, in __init__
    self.client = client.AptClient()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1041, in __init__
    self.bus = dbus.SystemBus()
  File "/usr/lib/pymodules/python2.7/dbus/_dbus.py", line 202, in __new__
    private=private)
  File "/usr/lib/pymodules/python2.7/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /usr/var/run/dbus/system_bus_socket: No such file or directory

---

### Post by lisati on 2012-01-02
Please start a new thread: technology changes in the space of two years, and what works for one release does not always work the same (or at all) in a newer release.

---

