---
title: "LCD 32 inch as pc monitor"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by peterthewolf on 2008-03-02
I am using a samsung 32in lcd tv as the pc monitor but I have to keep hold of an old crt as no linux live cd that I know of can load successfully using the lcd. The puzzle is that all distros can use the lcd while loading.
A good example is partedmagic which shows a nice high def display while loading but when it has loaded it looses the display. Ubuntu does likewise.

I do not need a cure but an explanation would be nice.

---

### Post by Rocket2DMn on 2008-03-03
LiveCDs don't come with full support for all hardware, and video drivers seem to be especially lacking.  Once installed, it is generally easy to get graphics cards and monitors working together well, but LiveCD support is just limited (there's only so much you can fit on 700MB).

---

### Post by peterthewolf on 2008-03-03
Yes and no, when I install any distro I have tried I cannot set the LCD until after install so I still need the CRT for install.

---

### Post by Rocket2DMn on 2008-03-03
You can try using alternate install CDs which don't have a live session, these work on a much wider range of hardware because it doesn't load an X-server.  Although there are no guarantees, I bet you would have much better luck using those text based installers, then you can reconfigure X once you've installed.

---

