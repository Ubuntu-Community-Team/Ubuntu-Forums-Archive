---
title: "Configuring X11 to allow a high screen resolution."
date: 2008-10-31
forum: Hardware
---

### Post by Professor Bacon on 2008-10-31
Greetings, Ubuntu users. Recently, I've installed Ubuntu on my laptop in a dual-boot configuration, and while everything does seem to be running smoothly, I am having a slight issue with the screen resolution, namely that it will not allow me to select anything higher than 800x600. Can any of you fine fellows assist me with configuring X11 to allow the display resolution of 1280x800 @ 60 Hz? I'm not sure if this information is necessary, but the screen is a 15.4 inch model mounted on an ASUS M50VM laptop.

---

### Post by cariboo on 2008-10-31
What version of Ubuntu are you using? If you are using 8.0.4.1 then press Alt-F2 and type:

```
sudo displayconfig-gtk
```

This should allow you to set the resolution.

Jim

---

### Post by Professor Bacon on 2008-10-31
> **cariboo907 said:**
> What version of Ubuntu are you using? If you are using 8.0.4.1 then press Alt-F2 and type:

```
sudo displayconfig-gtk
```

This should allow you to set the resolution.

Jim

By Jove, that's it! Thank you for your support, good sir. I'll be sure to write that down.

---

