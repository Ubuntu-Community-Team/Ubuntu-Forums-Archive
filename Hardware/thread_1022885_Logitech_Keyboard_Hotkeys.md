---
title: "Logitech Keyboard Hotkeys"
date: 2008-12-27
forum: Hardware
---

### Post by PhiSI on 2008-12-27
Hi
I just installed ubuntu and now i'm trying to get my logitech keyboard to work correctly. The "normal" buttons wok just fine. But the hotkeys are messed up. Some are no recognized (no function) and other do things they are not supposed to do (e.g. "stop" starts an instant messeanger). After some searching I found the tool Key-Touch/Editor. Now to start configuring my keyboard i need to press the hotkeys so the software gets the keycode. But for some reason the "special" keycodes nefer reach the Key-Touch Editor. I guess there is some service running that intercepts them and starts the messed up functions any ideas how i can (temporarly) stop this?

---

### Post by teaker1s on 2008-12-30
```
xev
``` will give you output of key press
xmodmap will help
[https://help.ubuntu.com/community/MultimediaKeys]("https://help.ubuntu.com/community/MultimediaKeys")

---

