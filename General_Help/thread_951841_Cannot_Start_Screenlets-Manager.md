---
title: "Cannot Start Screenlets-Manager"
date: 2008-10-18
forum: General Help
---

### Post by cangel0612 on 2008-10-18
Hello all,

I am trying to start screenlets-manager, but it will only run with sudo. It doesn't have any functionality there, and I really don't like the idea of running too many things in sudo. 

Here is the error I keep getting:

It looks like you are running gnome
/home/ender/.config/autostart/Screenlets Daemon.desktop
/home/ender/.config/autostart/screenlets-daemon.desktop
False
Create autostarter for: Screenlets Daemon
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1201, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 267, in __init__
    self.lookup_daemon_autostart()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 299, in lookup_daemon_autostart
    f = open(starter, 'w')
IOError: [Errno 13] Permission denied: '/home/ender/.config/autostart/Screenlets Daemon.desktop'


Let me know what you come up with .... Thanks!

---

