---
title: "emacs &lt;ctrl&gt;-_ (undo) don't work on text mode"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by lls_draco on 2007-11-24
Hi People,

I configured my keyboard (pt) in gnome via System->Preferences->Keyboard.

I have a sony vaio VGN_B1XP with portuguese keyboard layout. And when I use emacs in a text mode, using gnome-terminal, I cannot undo (<ctrl>-_ keybind). The strange thing is that in graphical mode this problem doesn't appear.

I'll appreciate any hint for it.

Thanks in advance.

lls_draco.

---

### Post by troelskn on 2008-01-03
I have the same problem, with Danish keyboard settings. I appears that, if I press <ctrl>+<shift>+<The key, two places left of backspace> it works. Incidentally,  that's where the underscore sits, with US keyboard. One might assume then, that I have US keyboard, but that's _not_ the case, since all other characters come out, as they should.

I'm guessing this is related to gnome-terminal, rather than emacs. Any ideas?

---

### Post by troelskn on 2008-01-03
I figured it out. I have Danish as default keymap, but still have US in the list (System > Preferences > Keyboard > Layouts). For some reason, pressing the ctrl key, temporarily changes from Danish to US keymap. I deleted the US keymap from the list and now it works. Weird, but there you have it.

---

### Post by lls_draco on 2008-01-03
It also cured my problem ... :-) I'd never thought about that. I think I'll only reach that solution by chance.

   Thank you very much,

P.S. - I think this problem is a weir unresolved bug. Maybe Unbuntu developers should take a look at it.

---

