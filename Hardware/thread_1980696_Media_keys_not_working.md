---
title: "Media keys not working"
date: 2012-05-15
forum: Hardware
---

### Post by Park Bom on 2012-05-15
Hello Ubuntu Forums!

What are the commands that I should be mapping to my previous, pause, stop, next, and mute keys on my HP Pavilion dv6 laptop? I already did the volume up/down keys

[IMG]http://i.imgur.com/OoQQi.png[/IMG]

but I don't know what it would be for the others.

Thanks for any help!

---

### Post by Toz on 2012-05-16
You have, I believe, two choices:

1. According to /usr/include/X11/keysymdef.h and/or [http://wiki.linuxquestions.org/wiki/XF86_keyboard_symbols]("http://wiki.linuxquestions.org/wiki/XF86_keyboard_symbols"), here is a list of XF86 keyboard symbols you can try.

2. Depending on the music player you are using, you can use built-in controls. For example, for gmusicbrowser you can use dbus-send (make sure you have the MPRIS2 plugin enabled) like this:

- previous = ```
dbus-send --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.RunCommand string:PrevSong
```
- stop = ```
dbus-send --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.RunCommand string:Stop
```
- Play/Pause (or mute) = ```
dbus-send --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.RunCommand string:PlayPause
```
- next = ```
dbus-send --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.RunCommand string:NextSong
```

---

