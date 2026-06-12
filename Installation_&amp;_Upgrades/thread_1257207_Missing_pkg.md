---
title: "Missing pkg"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by scpatl4now on 2009-09-03
I get the following output at the end of trying to complile the new F-spot:

checking for F... configure: error: Package requirements (libgnome-2.0 >= 2.2 libgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtk-sharp-2.0 >= 2.12.2 glib-sharp-2.0 >= 2.12.2 glade-sharp-2.0 >= 2.12.2 gnome-vfs-sharp-2.0 >= 2.12.2 gtk+-2.0 >= 2.14 mono >= 2.0.0 mono-cairo >= 1.2.4) were not met:

No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libexif' found
No package 'libexif' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

What package am I missing?
(I'm kinda new at this type of stuff)**[B]**[/B]

---

### Post by Keith Hedger on 2009-09-03
```
sudo apt-get build-dep f-spot
```

---

### Post by scpatl4now on 2009-09-03
> **Keith Hedger said:**
> ```
sudo apt-get build-dep f-spot
```
I figured it out thanks (and I know how to install via 'apt-get' but thanks anyhow).  I have the older version, and wanted to check out the newer one.  I actually got past the ./configure step but got errors trying to get past "make" so I gave up (for now).  It was a good learning exercise though, and I feel confident that I could do it with something else if I had to

---

