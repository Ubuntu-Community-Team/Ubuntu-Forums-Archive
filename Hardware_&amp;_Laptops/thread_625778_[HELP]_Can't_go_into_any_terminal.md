---
title: "[HELP] Can't go into any terminal"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by JhonQ on 2007-11-28
hi, if I press "ctrl+alt+f1" I only get a black screnn. What's that? where's the terminal?.
Kubuntu Gutsy, nvidia fx 5200 driver mounted by ENVY. Compiz-fusion working.

---

### Post by subs on 2007-11-28
> **JhonQ said:**
> hi, if I press "ctrl+alt+f1" I only get a black screnn. What's that? where's the terminal?.
Kubuntu Gutsy, nvidia fx 5200 driver mounted by ENVY. Compiz-fusion working.

ctrl+alt+f1 kills the running instance of xserver..... so it shows u a raw version of ur OS with all the GUI stripped down..... to restart to gui just say "startx"

---

### Post by Linicks on 2007-11-28
> **subs said:**
> ctrl+alt+f1 kills the running instance of xserver....

No it doesn't, it should bring up a terminal.

**Subs:** What happens after Ctrl+Alt+F1 if you use Alt+rightarrow to scroll through the terminals?  Blackscreen on all?  It maybe the terminal F1 is assigned is the root of the current X.

Nick

---

### Post by JhonQ on 2007-11-28
F1 to F6 are in black screens. I´ve tried tiping in, by mind, my login and password, but nthing happens

---

### Post by nickelby on 2007-11-28
Just a question, do you have "vga=791 (or whatever value)" in your /boot/grub/menu.lst under your kernel options? If you do, perhaps you can try removing it and see whether that works.

---

