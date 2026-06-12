---
title: "Inhibiting gnome-screensaver via DBus"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by jazzgossen on 2006-12-07
I'm trying to write a script that will inhibit gnome-screensaver when running on battery power, in order to save CPU cycles. 

I tried to run 

dbus-send --system --print-reply --dest=org.gnome.Screensaver /org/gnome/Screensaver org.gnome.Screensaver.Inhibit

but got the reply

Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Screensaver was not provided by any .service files

Indeed, running "locate .service" doesn't show anything that looks related to gnome-screensaver. But then, how can I control its behaviour?

---

### Post by 23meg on 2006-12-07
Mind the capitalization on the DBUS interface and service names; it should be *org.gnome.ScreenSaver* and */org/gnome/ScreenSaver*.

---

### Post by jazzgossen on 2006-12-07
Even when using ScreenSaver instead of Screensaver, I get the same result. There are no .service files related to ScreenSaver, either.

---

### Post by jazzgossen on 2006-12-07
Oh. Using --session instead of --system seems to work better. But there are more problems. Running:

dbus-send --session --print-reply --dest=org.gnome.ScreenSaver /org/gnome/ScreenSaver org.gnome.ScreenSaver.Inhibit string:"" string:"Running on battery"

gives me:

method return sender=:1.13 -> dest=:1.39
   uint32 1576439817
Applications can not close shared connections.  Please fix this in your app.  Ignoring close request and continuing.

So I get a cookie back and all seems fine, except for the "can not close shared connections" bit. I googled around for this and couldn't find a solution or an explanation of what it comes from. And after running this, the screensaver still gets activated.

Any more ideas?

---

### Post by 23meg on 2006-12-07
What exactly are you getting?

---

### Post by jazzgossen on 2006-12-07
(I edited my last message before I saw that you had already answered. Please see my post above.)

---

### Post by 23meg on 2006-12-07
I tried that and I'm getting the same. See if the script in [this thread]("http://www.ubuntuforums.org/showthread.php?t=284804") works for you. If it does, you may be able to modify it for your purpose, or it may give you an idea why things aren't working as supposed.

---

