---
title: "Where does Xorg save it's resolution settings now?"
date: 2009-10-07
forum: Hardware
---

### Post by bakegoodz on 2009-10-07
Where is resolution settings stored now??? It's not in xorg.conf anymore!
I changed my resolution now I can't see gnome when it loads. I can ssh in and make changes though.
I tried setting the monitors section in xorg.conf, with no effect.

 Don't tell me to:
  To use xrandr, it doesn't work from a non gnome-terminal.
  To rm ~/.config/monitors.xml, Ubuntu 8.04 doesn't have this config file to remove. 
  Get another monitor, I've tried 5 different ones from neighbors and friends.
  No I didn't setup Remote Desktop
  No I will not reinstall

---

### Post by wojox on 2009-10-07
Just reset X:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bakegoodz on 2009-10-27
That will just reconfigure the keyboard

---

