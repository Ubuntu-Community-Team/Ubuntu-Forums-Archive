---
title: "aterm and swedish letters"
date: 2005-11-10
forum: General Help
---

### Post by yohan on 2005-11-10
Ive installed ubuntu 5.10 AMD64 version and swedish letters work fine in the gnome terminal but I also installed aterm on this machine. In school we have red hat and i installed aterm there with good success and åäö works fine there. My problem is that swedish letters seem to work any application except aterm. How can I fix this? Did anyone else have this problem?

Thank you so much...its so annoying, i cant use irssi, vim or any app that requires aterm...:/

Thanks!

---

### Post by yohan on 2005-11-17
In case somebody cares, I solved it by using urxvt instead. Aterm is not UTF-8 only compatible.

---

### Post by hw-tph on 2005-11-18
You should be able to run **dpkg-reconfigure locales** and select Swedish (in addition to the english locales already selected). After the locales are regenerated, try launching aterm with LC_CTYPE set to sv_SE, like this: **LC_CTYPE="sv_SE" aterm &**

H&#229;kan

---

### Post by m3ck4rn on 2005-12-07
how do I add LC_CTYPE="sv_SE" to the buttom I start Aterm with?
so that i don't have to first start Aterm and then start anothether Aterm with the LC_CTYPE="sv_SE" aterm & command...

---

### Post by yohan on 2005-12-08
it works now! Tack Håkan!

You could add this alias to your .bashrc:
alias aterm='LC_CTYPE="sv_SE" aterm'

---

