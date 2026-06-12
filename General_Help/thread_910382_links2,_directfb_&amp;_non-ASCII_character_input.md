---
title: "links2, directfb &amp; non-ASCII character input"
date: 2008-09-04
forum: General Help
---

### Post by Hakimio on 2008-09-04
I have changed console keymap and now I can type my native language characters in console and console applications (vim, emacs, mc, lynx, elinks and links2 in text mode, etc), but it doesn't seem to work in direct framebuffer. When using links2 with directfb driver unicode chars are displayed correctly in web pages, but when I try to type any non-ASCII characters nothing happens. What am I missing?
Any help appreciated!

---

### Post by Hakimio on 2008-09-05
Up

---

### Post by Hakimio on 2008-09-06
Up

---

### Post by Vivaldi Gloria on 2008-09-06
> **Hakimio said:**
> but when I try to type any non-ASCII characters nothing happens. 

I'm also curious about this. When I use non-english letters I get garbage. How does one change the keyboard layout in fb?

---

### Post by Hakimio on 2008-09-07
> **Vivaldi Gloria said:**
> I'm also curious about this. When I use non-english letters I get garbage. How does one change the keyboard layout in fb?
Well, I too get garbage when using driver fb and nothing shows up when directfb is used.
I think the problem is not related to changing keyboard layout but to the lack of fonts. Console uses fonts located in /etc/console-setup & /usr/share/consolefonts/ while directfb, I guess, stores its in /usr/lib/directfb-1.0-0/interfaces/IDirectFBFont/ . While libdirectfb-extra adds more of those fonts, it doesn't seem to help.

Maybe someone knows how to add more of these fonts?

---

