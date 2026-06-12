---
title: "Motherboard id"
date: 2009-11-30
forum: Hardware
---

### Post by mikee55 on 2009-11-30
I've got Karmic running on my system, I don't know anything about the motherboard I'm using. It has no names printed on it, and its not in its original case. How can I find it out?

Cheers

Mike :)

---

### Post by sisco311 on 2009-11-30
```
sudo lshw -class bus
```

Or install [hardinfo]("apt://hardinfo") (apturl link), a GUI application that displays information about your hardware.

---

### Post by Kevbert on 2009-11-30
Another command is
```
sudo dmidecode | less
```
which gets info via the BIOS.

---

### Post by mikee55 on 2009-11-30
Thanks, Id remains blank or unknown, I ran Everest as well in Wine, but no joy????????????????????

---

