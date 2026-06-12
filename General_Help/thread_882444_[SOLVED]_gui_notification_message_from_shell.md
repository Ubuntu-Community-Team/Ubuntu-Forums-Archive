---
title: "[SOLVED] gui notification message from shell"
date: 2008-08-07
forum: General Help
---

### Post by lavinog on 2008-08-07
Is there a shell command that will allow me to send a popup message to the desktop?
I am looking for a way to allow some custom scripts to send alerts, or notify users through a ssh term that I will be doing something that will affect the system

---

### Post by kaibob on 2008-08-07
I don't know what ssh term is, but both zenity and xmessage can be used for messages, and I believe both are installed in Hardy by default. 

For zenity:

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

For xmessage, see the man page.

---

### Post by lavinog on 2008-08-16
Zenity looks like it will work for me.
I can't get it to display on another users desktop though. For example: If a user is logged on and I do some maintenance remotely. I want to be able to send a message to his desktop explaining that I am doing maintenance.

---

### Post by spupy on 2008-08-16
Also try **notify-send**
For example:
```
notify-send --icon=gtk-info --urgency=low --expire-time=3000 "You have no new mail"
```

This will display a pop-up like in the lower right corner of the screen. It disappears by itself after expire-time. 

It is part of the **libnotify** package.

---

