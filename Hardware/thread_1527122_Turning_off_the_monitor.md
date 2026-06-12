---
title: "Turning off the monitor?"
date: 2010-07-08
forum: Hardware
---

### Post by Struwelpeter on 2010-07-08
Is there a way to immediately turn off the monitor? I often leave download software on my Compaq HP 6715s, and it would be nice to have a quick way to turn off the monitor at will, instead of having to leave it to screensaver settings.

---

### Post by nemilar on 2010-07-08
Try this:

```
xset -display :0 dpms force off
```

This would only work inside X, I think...  And if your display is something other than :0, you'll need to adjust the command accordingly.

---

### Post by Struwelpeter on 2010-07-09
It did work. Thanks!

---

### Post by Struwelpeter on 2010-07-10
Strange... That worked, at first, but now the monitor doesn't stay off for longer than 1 minute. And -- perhaps unrelatedly -- I have noticed that my Screensaver (blankscreen) isn't working, either: it never starts.

Any clues?

---

### Post by _Mark_ on 2010-07-10
This is from memory so may not be an option, if you go into Power Management, can you select just to turn off screen when lid is closed instead of suspend, hibernate etc

May be worth a look :D

---

### Post by Struwelpeter on 2010-07-11
Hmm, indeed the option is there. Might be a nice workaround, thanks!
I'm still baffled, however, as to why the heck Screensaver never turns on...
Cheers,
S.p.

---

