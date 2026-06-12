---
title: "[SOLVED] No Unicode for the console?"
date: 2008-11-30
forum: General Help
---

### Post by siddartha on 2008-11-30
I have noticed that in the traditional console (Alt+Ctrl+F1 for example) there's no unicode support. I have activated the framebuffer which makes the screen a little better than the ugly EGA. Still, there is no Unicode support. Should I go with fbiterm instead of getty?

---

### Post by KeyserSoze93 on 2008-11-30
try:
```
unicode_start
```

---

### Post by siddartha on 2008-11-30
First there was no change. Than I modified the used font (not all unicode fonts have the chars I need) and everything went allright.

---

### Post by siddartha on 2008-11-30
Oops. Actually Unicode is enabled in Ubuntu. The console font was the problem. That, with a framebuffer activated it makes for a pretty console.

---

### Post by siddartha on 2008-11-30
The important command here was to find the installed console fonts: ```
locate psf| grep console
``` than use the ```
setfont
``` comand.

---

