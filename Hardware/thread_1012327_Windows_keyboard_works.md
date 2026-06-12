---
title: "Windows keyboard works?"
date: 2008-12-15
forum: Hardware
---

### Post by fjm03 on 2008-12-15
One of the keys was sticking on my regular  US 101 keyboard so I temporarily attached a Logitech Elite keyboard to my desktop and 8.10 recognized almost all of the special function keys (Media, Play/Pause, Mute, Volume, E-Mail, Webcam and WWW). Why?

Oddly, a virtual copy of XP, running through VMware on the same physical machine did not.

---

### Post by tommcd on 2008-12-16
This may not be the most "technical" answer, but as I understand it, the newest versions of X-windows that ships with Ubuntu automatically detects the monitor, keyboard, and mouse without the need to configure them in xorg.conf. In fact, my laptop did not even have a xorg.conf file when I installed Ubuntu 8.10 on it.
In the past, you would have had to edit the keyboard section of xorg.conf if you changed to a different type of keyboard with different keys. This stuff is mostly automatic now.

---

### Post by fjm03 on 2008-12-16
Thanks. I was taken back since I didn't think there was a convention among OSs. I'm guessing a member of the open source community had the same keyboard and took the time to write the code.

---

