---
title: "Jocky-GTK Error trying to get drivers (12.04.1)"
date: 2013-01-27
forum: Hardware
---

### Post by ooleyguy on 2013-01-27
I used the command: sean@elric:~$ sudo jockey-gtk
and go the following error text:
```
(jockey-gtk:31624): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:31624): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 275, in update_tree_model
    info = self.get_ui_driver_info(h_id)
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 295, in get_ui_driver_info
    info = self.backend().handler_info(handler_id)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 264, in handler_info
    'used': str(h.used()),
  File "/usr/share/jockey/handlers/nvidia.py", line 130, in recommended
    subprocess.call(['update-initramfs', '-u', '-k', os.uname()[2]])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 149, in getData
    name_parts = package.name.split('-')
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 87, in __get_value_from_name
    v = int(name)
ValueError: invalid literal for int() with base 10: 'experimental-304'

```

If jockey-gtk won't let me install drivers, what do I do?

---

### Post by Yellow Pasque on 2013-01-27
Try gksu or gksudo instead of sudo..

---

