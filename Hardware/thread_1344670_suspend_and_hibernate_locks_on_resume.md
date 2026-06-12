---
title: "suspend and hibernate locks on resume"
date: 2009-12-03
forum: Hardware
---

### Post by Docaltmed on 2009-12-03
All the threads I've found say this problem is fixed in Karmic.

It isn't.

I'm running an HP TX2500 with a fresh install of Karmic. Suspend and hibernate don't work; the keyboard locks up on resume.

Any suggestions?

---

### Post by cenzorrll on 2009-12-18
sorry if this is a bit late, but here's how i fixed mine

in a terminal enter:

```
gksu gedit /etc/default/grub
```

then there should be a line that says: GRUB_CMDLINE_LINUX_DEFAULT

in the quotes add "i8042.reset"

it should then look something like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset"
```
next, type:
```
sudo update-grub
```
and restart, everything should be working now

---

### Post by Docaltmed on 2009-12-19
Thank you, Cenzorrl! That did the trick quite nicely!

---

