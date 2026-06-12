---
title: "X problem after upgrade kernel &amp; nvidia driver"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by vinboy on 2006-04-21
I just upgraded my kernel to 2.6.16.7 and nvidia driver from nvidia website.
After installation, reboot and I was not able to see any GUI.
when i use the console to startx, i see the screen brighten alittle but showing no image at all.

- my Xorg.0.log end with the following:
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
---------------------------------------------------

I suppose there is no error as far as the log shows, but it just stop loading when it reach the GLX part, usually it will continue to load keyboard etc.

I was able to normally startx to KDE after commenting out the GLX extension.
:-\"

---

