---
title: "Mouse slow after upgrade this morning"
date: 2005-01-19
forum: Hardware &amp; Laptops
---

### Post by crypticreign on 2005-01-19
Hoary - Dell Inpsiron 5000, 2.6.10

I runt apt-get ugprade about twice a day, every day.. after running it this morning, my mouse is a lot slower than it was last night(I am guessing a new upgraded package caused this).  It seems to be normal in gdm, but once gnome starts it slows way down.  It's hard to move.  I pushed the mouse acceleration up one notch, and then its way too fast.

I wanted to add... I just remembered that I did upgrade Xorg last night.  I bet that's it.  Hmm, what to do what to do

---

### Post by gerben on 2005-03-04
Same here. I haven't had time to figure out the cause, but there's la simple workaround. Issuing the command 'xset m 2 4' in an xterm speeds up the mouse. You can of course change the values 2 and 4, have a look at the xset man page.

Gerben.

---

