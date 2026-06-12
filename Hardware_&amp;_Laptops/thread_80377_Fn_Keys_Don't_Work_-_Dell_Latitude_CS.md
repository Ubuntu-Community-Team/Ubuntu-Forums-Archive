---
title: "Fn Keys Don't Work - Dell Latitude CS"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by Tsume on 2005-10-22
I read through the guide here:
[http://www.ubuntuforums.org/showthread.php?t=27039&highlight=multimedia+keys](http://www.ubuntuforums.org/showthread.php?t=27039&highlight=multimedia+keys)

I went to a real terminal... at least, I think that's what CTRL+ALT+F1 does as far as I know.  When I press the function keys, nothing happens.  I tried doing dmesg like it says, a bunch of stuff is spammed all over my screen and at the end there's a few lines saying too many keys are pressed (I'm not pressing anything).  The program 'xev' doesn't pick up my function keys, and neither does the hotkey manager thing in gnome.

Anything I can do to get working hotkeys?

---

### Post by Kebabji on 2005-11-04
just go to the apt manager and download I8kutils. it works perfectly :)

---

### Post by Kebabji on 2005-11-08
or try typing in 
"hotkeys -t inspiron8100"
at a terminal

---

