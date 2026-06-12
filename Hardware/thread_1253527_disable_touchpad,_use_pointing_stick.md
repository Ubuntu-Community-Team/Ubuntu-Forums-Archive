---
title: "disable touchpad, use pointing stick"
date: 2009-08-30
forum: Hardware
---

### Post by a__l__a__n on 2009-08-30
I would like to disable my touchpad (on a HP nc8430, under Ubuntu 9.04 64 bit) and use the pointing stick instead.  However, when I go to System->Preferences->Mouse->Touchpad and uncheck "Enable touchpad", my mouse buttons stop responding.  The pointing stick moves the cursor, but I cannot click on anything.  Ideas?

Thanks!

---

### Post by nymusicman on 2010-06-20
Other than asking the obvious question of "Are you using the buttons associated with your pointing stick?" try disabling it like this and see what happens.

```
$ xinput list
```

find the pointer you want to disable. then type...

```
$ xinput set-int-prop "your device name here" "Device Enabled" 8 0
```
to disable and... 
```
$ xinput set-int-prop "your device name here" "Device Enabled" 8 1
```
to enable.

See if that works. Did wonders disabling my pointing stick on my Dell D610.

---

