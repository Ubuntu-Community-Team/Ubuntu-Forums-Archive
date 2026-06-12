---
title: "install Ubuntu from Fedora"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2009-01-28
I got a system which already has Fedora Core 9 (64-bit) installed on it.

I want to replace it with intrepid/ubuntu-8.10-desktop-amd64.iso

I have downloaded the iso, but how can I install this Ubuntu without burning a CD.

Downloaded unetbootin-linux and did
chmod +x ./unetbootin-linux

But when I run ./unetbootin-linux as root on Fedora, nothing happens.
It just returns the command prompt.

---

### Post by albinootje on 2009-01-28
> **boondocks said:**
>  Downloaded unetbootin-linux and did
chmod +x ./unetbootin-linux

But when I run ./unetbootin-linux as root on Fedora, nothing happens.
It just returns the command prompt.

I just downloaded unetbootin-linux-307.
I've done this to run it as root (because Fedora probably doesn't have gksu) :
```

ssh -X root@localhost
chmod +x ./unetbootin-linux-307
./unetbootin-linux-307

```
and that worked.
(it did want mtools and p7zip-full installed actually).
unetbootin is a GUI application, so you need to give it proper access to your X.
Opening a terminal in Fedora, and then using "su -" will likely not work (unless Fedora made a workaround for that).

---

