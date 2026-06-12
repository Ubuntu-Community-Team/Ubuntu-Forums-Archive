---
title: "Change root PATH"
date: 2008-10-04
forum: General Help
---

### Post by reglacken on 2008-10-04
Using xfce

Changing my PATH has no effect as only root PATH is used.

How change root PATH, or how get system to use my PATH ?

If neither can be done, two root path directories /usr/local/bin 
and /usr/local/sbin are empty. May I safely use these ?


Keyboard shortcuts

How remove F1 and F9 as ubuntu short cuts: I have better use for these keys.

---

### Post by Locutus_of_Borg on 2008-10-04
add to your ~/.bash_profile a line ```
PATH="/usr/lib/ccache/bin:/opt/bin:/sbin:/usr/sbin:${PATH}"

```such as that

for the keyboard shortcuts check under system > preferences > keyboard for shortcuts and/or if you are using compiz, under general settings for the shortcuts, also use xbindkeys to set up any other key associations you might want

---

