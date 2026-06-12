---
title: "sudo nvidia-xconfig doesn't work"
date: 2008-09-11
forum: General Help
---

### Post by tone33 on 2008-09-11
So I'm trying to setup dual monitors on Kubuntu w/KDE4, which i can do just fine, just can't save to the etc/X11/xorg.conf file because i can't seem to start anything in root.  

i try this:
```
sudo nvidia-xconfig
```

and get this:
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

any ideas?

---

### Post by RedPandaFox on 2008-09-11
So you have the most recent drivers? Try

```
sudo nvidia-settings
```

---

### Post by dustigroove on 2008-09-11
```
sudo nvidia-settings
```

Cheers

---

### Post by tone33 on 2008-09-12
ah of course!  Somehow i knew that, but had forgotten.  thanks!

---

### Post by dustigroove on 2008-09-12
> **tone33 said:**
> ah of course!  Somehow i knew that, but had forgotten.  thanks!

Glad to help.  :)

---

