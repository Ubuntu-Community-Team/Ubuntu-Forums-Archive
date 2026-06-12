---
title: "installing xgl/beryl on a laptop?"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by superspak on 2006-12-19
is it possible to install xgl/beryl on a laptop with an intel extreme graphics chip?

---

### Post by groggyboy on 2006-12-19
try this in a terminal:
```
glxinfo | grep rendering
```
if it returns with a yes, then you can!  i have an intel 915gma video card on my laptop, and beryl runs fine.  i recommend you use aiglx though.  it has better support for intel cards than xgl does.

---

### Post by .t. on 2006-12-19
If you are on Edgy, you should be able to just set up the repo and install the "beryl" package. This will install everything you need. Run beryl-manager, start Beryl from the tray, and you should be good to go.

If you are using Dapper, it is slightly more complicated, as you need to install a new Xserver with AIGLX. This isn't hard - it's just one more package and a couple of config files to edit.

---

