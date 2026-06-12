---
title: "Resumes/reboots on its own"
date: 2016-10-11
forum: Hardware
---

### Post by greg66 on 2016-10-11
Greetings

I'm experiencing a weird behavior with pm functions:

- when requesting a suspend (both GUI and the pm-suspend command), the system goes to sleep, then wakes up after a period between 0 to a few minutes
- when requestion hibernate, the system shuts down then immediatly reboots normally (no resume)

I was running ububtu 12 and now I'm running ubuntu 16.04 on a new drive. Suspend to RAM used to work on ubuntu 12 but I don't see what could have broken it.

In the bios I disabled WOL.

How can I investiguate (and hopefully fix) this behavior?

Thanks in advance

---

### Post by greg66 on 2016-10-13
I found half of the solution, the "return from hibernate" part: it seems "grub-update" doesn't update grub, after manually updating grub, the computer returns from hibernation.
The suspend still doesn't work properly...

---

