---
title: "How do I disable LIBGL_ALWAYS_INDIRECT?"
date: 2011-02-05
forum: Hardware
---

### Post by IT-Joker on 2011-02-05
Hi all,
I've upgraded my graphic card to ATI Radeon HD 5570 and installed the latest Catalyst driver found on ATI website.

But I ran into problems running for example StarCraft 2 via Wine.

Wine complains about DirectDraw being turned off.
After a bit of searching I found this:
glxinfo | grep rendering
```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

When I do unset LIBGL_ALWAYS_INDIRECT and then launch StarCraft 2 from the terminal, it works.
But only for that terminal session.

How do I disable LIBGL_ALWAYS_INDIRECT permanently?
Thanks.

---

### Post by IT-Joker on 2011-03-02
Still no luck.
Haven't even found any config files containing text LIBGL_ALWAYS_INDIRECT.

I had nVidia driver before, is it possible that some part of it didn't uninstall and is now causing the problem?

---

### Post by Yellow Pasque on 2011-03-02
You may want to put this at the end of your ~/.bashrc
```
export LIBGL_ALWAYS_INDIRECT=no
```

---

