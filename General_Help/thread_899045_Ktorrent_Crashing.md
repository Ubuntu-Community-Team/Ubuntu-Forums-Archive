---
title: "Ktorrent Crashing"
date: 2008-08-23
forum: General Help
---

### Post by MarshyTheKid on 2008-08-23
I set up Ktorrent to start loading files automatically from my /tmp folder, which all of my Firefox downloads gets saved into. Once I started that, Ktorrent will start to load then it will crash.
When running ktorrent from the terminal I get
```
QObject::connect: Connecting from COMPAT signal (KComboBox::textChanged(QString))
ktorrent(10722): Couldn't start knotify from knotify4.desktop:  "KDEInit could not launch '/usr/lib/kde4/bin/knotify4'." 

<unknown program name>(10721)/: Communication problem with  "ktorrent" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

```

---

### Post by MarshyTheKid on 2008-08-24
When I run it, a dialog pops up for a second saying how it has crashed and it may be a corrupt torrent. In '.kde4/share/apps/ktorrent' I have moved all of the folders starting with tor into another folder, yet it still crashes.

---

### Post by MarshyTheKid on 2008-08-24
Any help?

---

### Post by MarshyTheKid on 2008-08-24
Nothing?

---

### Post by MarshyTheKid on 2008-08-25
Removing then reinstalling Ktorrent didn't fix this, neither did complete removal in Synaptic(its ktorrent-kde4).
Installing ktorrent does work and brings up my old torrents from my last installation of Ubuntu.

---

