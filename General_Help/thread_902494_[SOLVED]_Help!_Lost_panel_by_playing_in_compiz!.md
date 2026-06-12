---
title: "[SOLVED] Help! Lost panel by playing in compiz!"
date: 2008-08-27
forum: General Help
---

### Post by kai_kan on 2008-08-27
Absolute Newb here, but very into the linux philosophy. Please forgive my ignorance!

As I remember it, the last thing I did was enable the widget layer in advanced settings. I went in to look at my options and must have made a change, because I lost everything but my wallpaper and my pointer. There are no icons, no panel. I still see the effect of changing between workspaces, but there's nothing in either one. Even Alt+F2 brings up nothing.

Here's what I've tried in my effort to repair:

Did Ctrl+Alt+F1 to back out, then tried: ```
sudo apt-get remove compizconfig-settings-manager
``` which seemed to go through, but didn't solve my problem.

I'd appreciate any help. Ideally something that will get me back to where I was, but telling me whether there are folders I can back-up so I don't have to go through configuring my wifi, 3D graphics, etc. if I rebuild would be great.

Running dual-boot 8.04.1 with XP-MCE on Dell e1505 lappy.

Thanks in advance!

---

### Post by mocoloco on 2008-08-28
Maybe you already solved this by now, but try changing your session to "Failsafe GNOME" before logging in.  If that works you should be able to change your settings back to how they were, log back out and back in the default session.
If that doesn't solve it log in to a terminal as you've done before, and rename the folder that has your compiz settings, which would cause Ubuntu to create a new one with the default settings.
```
mv ~/.gconf/apps/compiz ~/.gconf/apps/compizOLD
```

---

### Post by lynx_hanan on 2008-08-28
Try starting the panel by typing gnome-panel in terminal

i lost it once too, but i didnt loose my icons

---

### Post by lynx_hanan on 2008-08-28
sudo apt-get purge compizconfig-settings-manager

will also remove the configuration files, maybe that mite help too

---

### Post by kai_kan on 2008-08-28
> **mocoloco said:**
> Maybe you already solved this by now, but try changing your session to "Failsafe GNOME" before logging in.  If that works you should be able to change your settings back to how they were, log back out and back in the default session.


Failsafe GNOME did it. A little embarrassed by the simplicity of the solution, but hey... I told you I was a newb! Re-installed compizconfig from there and disabled widget layer. All was well when I rebooted. Will probably wait a while before playing with settings I don't understand. ;)

Thanks for starting with the basics and getting me in. Happily back on the Ubuntu map.

Thanks as well to lynx_hanan for the effort!

---

