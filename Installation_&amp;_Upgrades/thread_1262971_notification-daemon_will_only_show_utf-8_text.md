---
title: "notification-daemon will only show utf-8 text"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Nephiel on 2009-09-10
I have this issue that has been bugging me for a while.

I run jaunty. My locale is ISO-8859-1, and all programs seem OK with that, I can type Spanish characters such as 'ñ' and 'á' everywhere, no problem. I have the notification-daemon and the notify-send binary installed through synaptic.

When I run this:
```
$ notify-send 'title' 'this is a notification message'
```
it will work just fine, displaying a little notification window. But if I do the same in Spanish:
```
$ notify-send 'título' 'esto es un mensaje de notificación'
```
nothing will happen, no window will appear, no error message will be shown. I've narrowed it down to the accented characters. This workaround makes the notification show correctly if you have the "recode" binary installed:
```
$ notify-send "`echo 'título'|recode ..UTF-8`" "`echo 'esto es un mensaje de notificación'|recode ..UTF-8`"
```

This leads me to believe that there is a bug with non-UTF-8 text either in the notify-send, libnotify or notification-daemon packages, but I don't know which one.

Could anyone try to reproduce this? We might have to file a bug report. For now I'm trying to figure out how to add a local diversion of notify-send and replace it with a wrapper that does the recoding and then calls the diverted binary.

---

