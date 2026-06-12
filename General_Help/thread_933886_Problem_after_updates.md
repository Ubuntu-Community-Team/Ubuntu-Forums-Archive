---
title: "Problem after updates"
date: 2008-09-29
forum: General Help
---

### Post by aknapp on 2008-09-29
I am experiencing problems after running the update feature. I am not sure what it updated, maybe someone can tell me where I can find a log for apt? The problems I'm having are:

- Dbus doesn't seem to be starting when I boot up.
- When I push the power button, instead of getting the nice prompt (log-off, hibernate, sleep, etc) menu, it just kills everything and shuts down.
- Also, when I plug in a usb device it doesn't show in "Computer"

Please help! :|

---

### Post by Pelham123 on 2008-09-30
> **aknapp said:**
> where I can find a log for apt? 

/var/log/dpkg.log

--------------------------------------------------------------------

> **aknapp said:**
> Dbus doesn't seem to be starting when I boot up.

But presumably starts with ```
sudo /etc/init.d/dbus start
```

and it is also listed in /etc/rc2.d/ with an 'S' prefix? (eg S12dbus) then it might be worth posting as a bug.

--------------------------------------------------------------------

Not sure about the power off yet. 

With the USB icons not appearing under 'Computer' they are mounted? You can access them? But just no icon?

---

### Post by sd401k on 2008-09-30
Same problem here. Everything comes up o.k. upon boot but I have no access to anything on the desktop.

---

### Post by aknapp on 2008-10-01
[quote=log file]
2008-09-28 06:22:01 startup archives unpack
2008-09-28 06:22:18 upgrade libdbus-1-3 1.1.20-1ubuntu2 1.1.20-1ubuntu2
2008-09-28 06:22:18 status half-configured libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:18 status unpacked libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:18 status half-installed libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:18 status half-installed libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:18 status unpacked libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:18 status unpacked libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:19 upgrade dbus 1.1.20-1ubuntu2 1.1.20-1ubuntu2
2008-09-28 06:22:19 status half-configured dbus 1.1.20-1ubuntu2
2008-09-28 06:22:19 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:19 status half-installed dbus 1.1.20-1ubuntu2
2008-09-28 06:22:19 status half-installed dbus 1.1.20-1ubuntu2
2008-09-28 06:22:19 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:19 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:19 upgrade system-tools-backends 2.6.0-0ubuntu7 2.6.0-0ubuntu7
2008-09-28 06:22:19 status half-configured system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:19 status unpacked system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:19 status half-installed system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:19 status half-installed system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:19 status unpacked system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:19 status unpacked system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:20 upgrade gnome-system-tools 2.22.0-0ubuntu9 2.22.0-0ubuntu9
2008-09-28 06:22:20 status half-configured gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:29 status unpacked gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:31 status half-installed gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:31 status half-installed gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:34 status unpacked gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:34 status unpacked gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:35 startup packages configure
2008-09-28 06:22:35 configure libdbus-1-3 1.1.20-1ubuntu2 1.1.20-1ubuntu2
2008-09-28 06:22:35 status unpacked libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:35 status half-configured libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:35 status installed libdbus-1-3 1.1.20-1ubuntu2
2008-09-28 06:22:35 status triggers-pending libc6 2.7-10ubuntu4
2008-09-28 06:22:35 configure dbus 1.1.20-1ubuntu2 1.1.20-1ubuntu2
2008-09-28 06:22:35 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:35 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:35 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:35 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:35 status unpacked dbus 1.1.20-1ubuntu2
2008-09-28 06:22:35 status half-configured dbus 1.1.20-1ubuntu2
2008-09-28 06:22:38 status installed dbus 1.1.20-1ubuntu2
2008-09-28 06:22:38 configure system-tools-backends 2.6.0-0ubuntu7 2.6.0-0ubuntu7
2008-09-28 06:22:38 status unpacked system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:38 status unpacked system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:38 status unpacked system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:38 status half-configured system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:38 status installed system-tools-backends 2.6.0-0ubuntu7
2008-09-28 06:22:38 configure gnome-system-tools 2.22.0-0ubuntu9 2.22.0-0ubuntu9
2008-09-28 06:22:38 status unpacked gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:38 status unpacked gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:38 status half-configured gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:44 status installed gnome-system-tools 2.22.0-0ubuntu9
2008-09-28 06:22:46 trigproc libc6 2.7-10ubuntu4 2.7-10ubuntu4
2008-09-28 06:22:46 status half-configured libc6 2.7-10ubuntu4
2008-09-28 06:22:46 status installed libc6 2.7-10ubuntu4[/quote]

That is the contents of the log file.

[quote=Pelham123]But presumably starts with sudo /etc/init.d/dbus start[/quote]
Yes

[quote=Pelham123]and it is also listed in /etc/rc2.d/ with an 'S' prefix?[/quote]
No, I don't see it in there. How do I add it?

---

### Post by Yellow Pasque on 2008-10-01
sudo ln -s /etc/init.d/dbus /etc/rc2.d/S12dbus

EDIT: Make sure it's in /etc/rc5.d too

---

