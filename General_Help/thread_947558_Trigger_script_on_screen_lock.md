---
title: "Trigger script on screen lock?"
date: 2008-10-14
forum: General Help
---

### Post by gumpish on 2008-10-14
Is it possible to have a script execute when the local X-Windows screen is locked?

I ask because I recently brought my cheap webcam into my office and installed the package "motion" (which makes your webcam a security camera by recording frames when there is motion) and it would be cool if I could have it automatically kick in whenever I lock the screen, and deactivate when I unlock it.

If this can't be done directly, how about triggering a script with a special keyboard shortcut? (For instance, the same one I use to lock the screen, CTRL+ALT+L...

---

### Post by gumpish on 2008-10-14
Looks like I can accomplish this by using dbus somehow.

dbus-monitor reports the following two events when the screen is locked and unlocked respectively:

```
signal sender=:1.9 -> dest=(null destination) path=/org/gnome/ScreenSaver; interface=org.gnome.ScreenSaver; member=SessionIdleChanged
   boolean true

signal sender=:1.9 -> dest=(null destination) path=/org/gnome/ScreenSaver; interface=org.gnome.ScreenSaver; member=SessionIdleChanged
   boolean false
```

Now I just need to find out how to monitor dbus messages and take action...

---

### Post by gumpish on 2008-10-15
Apparently this is mentioned in the Gnome ScreenSaver FAQ

[http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions](http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions)

---

