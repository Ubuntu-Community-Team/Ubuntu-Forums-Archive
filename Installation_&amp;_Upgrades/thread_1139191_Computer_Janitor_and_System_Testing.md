---
title: "Computer Janitor and System Testing"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by glantela on 2009-04-26
Hi Everyone, 

Just upgraded to Jaunty, mostly smooth transition- just 2 things:

Computer Janitor hangs my computer when i try to start it up, and the system testing doesnt want to start at all...

Anyone else have this issue?

---

### Post by glantela on 2009-04-26
Scratch that, the Janitor works now, must have been a freak hang or something... system testing gives me this in the terminal:

ari@lobo:~$ /usr/bin/checkbox-gtk
Traceback (most recent call last):
  File "/usr/share/checkbox/run", line 40, in <module>
    main()
  File "/usr/share/checkbox/run", line 35, in main
    application = manager.create_application(sys.argv)
  File "/usr/lib/python2.6/dist-packages/checkbox/application.py", line 153, in create_application
    return self.application_factory(config)
  File "/usr/lib/python2.6/dist-packages/checkbox/application.py", line 70, in __init__
    self.reactor, self.registry)
  File "/usr/lib/python2.6/dist-packages/checkbox/plugin.py", line 41, in __init__
    module.register(self)
  File "/usr/share/checkbox/plugins/backend_manager.py", line 65, in register
    self.dbus_name = dbus.service.BusName(self.DBUS_BUS_NAME, self.bus)
  File "/var/lib/python-support/python2.6/dbus/service.py", line 129, in __new__
    retval = bus.request_name(name, name_flags)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 306, in request_name
    'su', (name, flags))
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Connection ":1.60" is not allowed to own the service "com.ubuntu.checkbox" due to security policies in the configuration file

---

### Post by hapaboy408 on 2009-04-29
run as sudo

---

### Post by Dragonbite on 2009-04-29
What does janitor do?

---

### Post by Foxcow on 2009-05-02
> **Dragonbite said:**
> What does janitor do?

I'm curious as well.  I am afraid to break something by allowing it to clean the items it wants to clean up.

---

### Post by kva on 2010-08-08
Check your BIOS setting for 'Non-Execute Memory Protected' if it is Enabled then Disabled it...

---

### Post by Ginsu543 on 2010-08-09
Computer Janitor is pretty much useless in my opinion. It's supposed to help "clean up" your Ubuntu system, but what it does is delete software that has been installed apart from the main repositories (for example, programs installed from PPA's or from .deb packages). As a result, it can delete something you actually want to keep. I suggest you use Synaptic to remove unwanted software so that you know exactly what you are removing.

---

