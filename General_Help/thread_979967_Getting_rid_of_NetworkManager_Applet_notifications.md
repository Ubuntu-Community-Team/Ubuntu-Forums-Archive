---
title: "Getting rid of NetworkManager Applet notifications"
date: 2008-11-12
forum: General Help
---

### Post by marcb on 2008-11-12
I am trying to disable NetworkManager Applet notifications, for example, when it connects to a wireless network, but I can't find anywhere how to do it.

There is this post of another person interested in it:
**[http://ubuntuforums.org/showthread.php?t=961416&highlight=Applet+notifications](http://ubuntuforums.org/showthread.php?t=961416&highlight=Applet+notifications)**, but the thread is closed because it is in Intrepid's Development forum and Intrepid has already been released...

Does anyone know how can I do it?

Thank you very much in advance! :-)

---

### Post by mar2000 on 2008-11-29
I also wish I knew how to get rid of the annoying notifications. I don't like the computer telling me it was successful in connecting to the network every time the gdm starts.

---

### Post by sdennie on 2008-11-29
It's possible to brute force this behavior but, it will disable *all* notifications:

```

sudo chmod -r /usr/share/dbus-1/services/org.freedesktop.Notifications.service

```

Edit:
It's -r not -x

---

