---
title: "Ctrl-Alt-R doesn't generate a key press"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by pheitman on 2005-12-06
I'm not sure whether this is an X question or not, but under xemacs Ctrl-Alt-R isn't visible. That is, if I do a M-X describe-key, Ctrl-Alt-R doesn't get seen. Ctrl-Alt-E and Ctrl-Alt-T (the two keys to either side of R) do get seen - but not R. Any ideas? I'd really like to get Ctrl-Alt-R back...

Peter

---

### Post by pheitman on 2005-12-12
I finally figured this out. It turns out the kde has a set of "Global Shortcuts" in .kde/shared/config/kdeglobals. These are keyboard shortcuts for all kinds of thinkgs, including Alt+Ctrl+R. Changing the shortcuts to 'none' instead fixed the problem for me.

peter

---

### Post by earobinson on 2005-12-12
And you learn something every day :)

---

