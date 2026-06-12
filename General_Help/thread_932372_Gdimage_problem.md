---
title: "Gdimage problem"
date: 2008-09-28
forum: General Help
---

### Post by djh82uk on 2008-09-28
Hi guys

Im trying to setup "PHPMotion", it used gdimage to make captcha images but it needs gdimage compiled with freetext I beleive, now everything about the site works but the captcha image just comes up with a red "X" placeholder.

I don't know how to compile it with freetext support, and i cannot un-install it to compile it as it is part of the "ubuntu-desktop" package.

Can anyone help?

---

### Post by kadeous on 2009-11-17
I'm having the same problem, I've installed php-gd, tried to compile php5 from source with gd support. I'm a complete noob to ubuntu or linux for that matter. Everything else works great. Anyone solve this problem?

---

### Post by kadeous on 2009-11-20
I fixed this issue by copying the font to the system font folder and reloading the font cache. Works now.

---

