---
title: "how to disable screen locking on resume?"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by pau on 2006-09-17
Hi,

have an IBM thinkpad and everything works very nice (well the fans is an issue, too much noise) but I'd like how to disable the screen locking on resumen after a suspend-to-ram. 

I have edited /etc/default/acpi-support and set
```

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true
```

but the screen is always locked and it annoys me... Any hint how to disable this locking?? Thanks!

---

### Post by ciscosurfer on 2006-09-17
Are you using xscreensaver or gnome-screensaver?  If you're using the latter, you can prevent this from happening by *unchecking* the box that says "Lock screen when screensaver is active."

---

### Post by pau on 2006-09-18
it's already unchecked! .... :(

---

### Post by pau on 2006-09-18
bump... nobody has an answer?

---

### Post by RafRaf on 2006-09-19
I disabled the screen lock with the configuration editor:

Application - System - Configuration editor:

Apps - gnome-power-manager - lock-on-suspend=unchecked, lock-on-hibernate=unchecked.

hope that helps!
cheers

---

### Post by pau on 2006-09-19
can you give me the path to that file?

I didn't understand whether it's a gui or a text file???

---

### Post by RafRaf on 2006-09-19
Oh sorry, it's an application. Open Applciations select System Tools and then Configuration Editor. 

If you dont see it in the Applications menu then do:

Applications and select Add/Remove to add Configuration Editor.

cheers!

---

