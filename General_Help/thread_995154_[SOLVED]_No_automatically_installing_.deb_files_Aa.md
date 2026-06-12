---
title: "[SOLVED] No automatically installing .deb files? Aagh!"
date: 2008-11-27
forum: General Help
---

### Post by Mulenmar on 2008-11-27
I install the Hardy version Ubuntu Server edition, and then installed wdm and xfce4.  But when I try to double-click on a .deb file and install it, it gives me basically a "search for application" box. Which application opens opens and installs these? I've used it a million times in typical installations, but never checked the name.:(

---

### Post by cmay on 2008-11-27
gdebi package installer  maybe

---

### Post by kostkon on 2008-11-27
> **Mulenmar said:**
> I install the Hardy version Ubuntu Server edition, and then installed wdm and xfce4.  But when I try to double-click on a .deb file and install it, it gives me basically a "search for application" box. Which application opens opens and installs these? I've used it a million times in typical installations, but never checked the name.:(
The application (that Ubuntu Desktop has by default) is [*gdebi*]("http://packages.ubuntu.com/hardy/gdebi"). It may work XCFE, it may not, I don't really now.

---

### Post by sisco311 on 2008-11-27
/usr/bin/gdebi-gtk

```
sudo aptitude install gdebi
```

---

### Post by Mulenmar on 2008-11-27
@ Kostkon

Yes, that's the one.

@sisco311

Thanks, that did the trick! 8~)

---

