---
title: "Lubuntu 13.10 touchpad config"
date: 2014-02-16
forum: Hardware
---

### Post by Rob Sayer on 2014-02-16
This may be a silly question ...

Installed lubuntu 13.10 last Wednesday on my Acer 1Gb netbook.  Previously had mint 16 Mate for a short time :rolleyes:.  Before that, xubuntu and kubuntu, 12.04 on.  Lubuntu is FAST.  So fast I'm inclined to forgive a few rough edges.

This netbook has the infamous Cedarview gpu and a broadcom 4313 (14e4:4727) wireless adapter, which doesn't have the best linux support either.  So I'm not afraid of configuration from terminal or gksudo.

I wanted to turn of the touchpad while typing and tap to click, so I opened ~/.config/lxsession/Lubuntu/autostart with leafpad as per:

[https://help.ubuntu.com/community/Lubuntu/Mouse](https://help.ubuntu.com/community/Lubuntu/Mouse)

... and the file was empty.  No entries.  File properties show the file is 4 bytes on disk.  I was expecting many items there.

If  I run

```
synclient -l
```

in terminal, there are a lot of parameters set.

What am I missing here?  Is it normal for this file to be there but empty?

---

### Post by ajgreeny on 2014-02-16
I can't help with turning of the touchpad while typing, but to stop "tap to click" make a script with content
```
#!/bin/bash
synclient MaxTapTime=0
```save it as notap, make it executable and put it in /usr/bin, and then add it to the list in /etc/xdg/lxsession/Lubuntu/autostart  in form ```
@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
[COLOR=#ff0000]@notap[/COLOR]
```

That's my full list so ignore all but the @notap at the bottom.

---

### Post by Rob Sayer on 2014-02-17
Thanks ... but I'm still wondering why the autostart config file in my home directory is empty.

---

### Post by kalehrl on 2014-02-17
Because auto-starting applications works differently in 13.10:
[http://askubuntu.com/questions/369319/how-to-disable-tap-to-click-in-lubuntu-13-10/369366#369366](http://askubuntu.com/questions/369319/how-to-disable-tap-to-click-in-lubuntu-13-10/369366#369366)

---

### Post by Rob Sayer on 2014-02-18
Aaah ... thanks.

---

