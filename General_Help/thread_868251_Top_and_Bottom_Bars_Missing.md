---
title: "Top and Bottom Bars Missing"
date: 2008-07-23
forum: General Help
---

### Post by mikelmahoo on 2008-07-23
I had to turn off my computer manually because it froze. When I turned it back on I got an error message that said nautilus isn't working. When my desktop came up the top and bottom bars were missing. 

I restarted and that didn't work. How do I get them back?

---

### Post by Darkade on 2008-07-23
Could you log in into a failsafe terminal and post the output of
```
nautilus
```

---

### Post by mikelmahoo on 2008-07-23
This is what it got me.

seahorse nautilus module initialized
Initializing nautilus-share extension
**(nautilus:5403): Warning**:Unable to add monitor Not Supported
**(nautilus:5403): Warning**:Can not calculate NET_NUMBER_OF_DESKTOPS
**(nautilus:5403): Warning**:Can not calculate NET_NUMBER_OF_DESKTOPS
**(nautilus:5403): Warning**:Can not get NET_Workarea
**(nautilus:5403): Warning**:CAn not determine work area, guessing at layout, Nautilus-Share-Message, Called "net user info" but it failed: net usershare returned error 255: net usershare: Can not open var/lib/samba/usershares, Error no such file or directory, Please ask administrator to enable usershares

---

### Post by Darkade on 2008-07-23
In the fail safe terminal try installing samba, there seems to be a problem with that
```
sudo apt-get install samba smbfs
```
and then restarting.

---

### Post by bruce89 on 2008-07-23
The panels are actually controlled by *gnome-panel* (suprisingly).

Running [FONT="Mono"]gnome-panel[/FONT] might output something interesting.

---

