---
title: "How do I disable my keyboard and touchpad?"
date: 2010-11-18
forum: Hardware
---

### Post by blacktrance on 2010-11-18
I have an Acer Aspire 8730. Its keyboard recently broke and I got a USB keyboard. It works fine, except the old keyboard sometimes connects. How do I disable it?
And how do I disable the touchpad?

---

### Post by SnickerSnack on 2010-11-18
Use xinput.  For example, my track point is disabled with

```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Device Enabled" 8 0
```

Run "xinput list" from the command line and it should give a big list of peripherals.  Use the man page for more info.  It's been a while since I had to use this (I wrote scripts to handle it for me).

---

