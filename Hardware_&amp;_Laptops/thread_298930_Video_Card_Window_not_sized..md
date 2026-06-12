---
title: "Video Card? Window not sized."
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by Kinn on 2006-11-13
I believe this is a video card problem. I have Kubuntu installed completely but not my only resolution option is 600x350 or something like that and my window takes up the top right part of my monitor leaving a large black space at the bottom and left side. Is there something I can do to correct this problem?

---

### Post by taurus on 2006-11-13
You probably need to install a driver for your graphic card and what is it anyway?

Otherwise, reconfigure your X again, from terminal, with

```
sudo dpkg-reconfigure xserver-xorg
```

---

