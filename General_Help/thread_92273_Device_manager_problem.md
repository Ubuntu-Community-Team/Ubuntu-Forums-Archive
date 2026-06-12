---
title: "Device manager problem"
date: 2005-11-19
forum: General Help
---

### Post by theh0g on 2005-11-19
I'm trying to run hal-device-manager and it doesn't work anymore. All I get is this:
```
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 14, in ?
    import LibGladeApplication
  File "/usr/share/hal/device-manager/LibGladeApplication.py", line 5, in ?
    from gtk import glade
ImportError: cannot import name glade

```

Anyone got an idea on what to do to fix this and make it work again?

---

### Post by theh0g on 2005-11-19
Anyone?

---

### Post by eitan on 2005-12-08
i just attempted to launch hal-device-manager (v0.5.3) and to my surprise
 i get this:

<gtk.Menu object (GtkMenu) at 0xb6afa0a4>
/usr/share/hal/device-manager/DeviceManager.py:45: GtkWarning: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
  LaunchpadIntegration.add_items (widget, -1, False, True);
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 18, in ?
    DeviceManager()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 70, in __init__
    lambda *args: self.gdl_changed("DeviceAdded", *args))
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 231, in connect_to_signal
    self._obj.connect_to_signal(signal_name, handler_function, dbus_interface, **keywords)
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 113, in connect_to_signal
    path=self._object_path,
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 138, in add_signal_receiver
    named_service = bus_object.GetNameOwner(named_service, dbus_interface='org.freedesktop.DBus')
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 64, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 379, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: Could not get owner of name 'org.freedesktop.Hal': no such name


wish i had the answer.. lots of things don't seem to be working these days.  it's frustrating.

---

