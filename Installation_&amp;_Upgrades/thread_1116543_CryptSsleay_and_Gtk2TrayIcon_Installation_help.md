---
title: "Crypt::Ssleay and Gtk2::TrayIcon Installation help"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by xr4v3nx on 2009-04-05
guys..can you help me install crypt::ssleay and gtk2::trayicon.. what are the step by step process..im not good at commands.are there any other way?coz checkgmail wont work without both of them. it detected that im missing those. i already have the both files but i dont know how to use it. im also new to linux.

---

### Post by Xero Xenith on 2009-04-17
Hmm... on mine it automatically picked up libcrypt-ssleay-perl and libgtk2-trayicon-perl - it didn't seem to need any more. Might be because I'm using Jaunty, but I'm not sure.

```
The following extra packages will be installed:
  libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl libemail-mime-encodings-perl libgtk2-sexy-perl libgtk2-trayicon-perl libmd5-perl libsexymm2
The following NEW packages will be installed
[...]

```

It then worked fine. Have you enabled Universe, Restricted and Multiverse in Software Sources?

---

### Post by xr4v3nx on 2009-04-18
"It then worked fine. Have you enabled Universe, Restricted and Multiverse in Software Sources?"

Sir, I don't know what are Universe, Restricted and Multiverse in Software Sources. I'm totally new to Linux, Ubuntu and stuff.

---

### Post by MyR on 2009-04-25
In System > Administration > Software Sources
make sure you are connected to the internet.
check the universe, restricted, and multiverse boxes then close. reload when it asks.

then go ahead and reinstall checkgmail

peace

---

