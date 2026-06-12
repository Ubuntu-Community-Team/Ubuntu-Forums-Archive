---
title: "[SOLVED] 'who' command shows me logged in multiple times"
date: 2008-11-11
forum: General Help
---

### Post by LunaEqualsLuna on 2008-11-11
when i do the who command on comp it shows me logged in 5 times!
Whats going on here? Shouldn't i only be logged on once?

This is the out put from 'who'

username    tty7         2008-11-12 01:35 (:0)
username    pts/0        2008-11-12 01:41 (:0.0)
username    pts/1        2008-11-12 01:43 (:0.0)
username    pts/4        2008-11-12 01:49 (:0.0)
username    pts/2        2008-11-12 02:01 (:0.0)

is this normal? and if not how do i sort it out.
ps this is after a restart :S

---

### Post by spibou on 2008-11-11
Yes it's normal and there's nothing to sort out. You could arrange for the shells which start on top of the terminal emulators that you're using not to be login shells. This may fix it. Which terminal emulator are you using?

---

### Post by fooey on 2008-11-11
Search command helps :)

[http://ubuntuforums.org/showthread.php?t=653020]("http://ubuntuforums.org/showthread.php?t=653020")

---

### Post by LunaEqualsLuna on 2008-11-11
thx that clears things up!

---

