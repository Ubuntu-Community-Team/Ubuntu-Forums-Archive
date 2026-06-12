---
title: "[SOLVED] 8.10 nVIDIA - visual effects bug??"
date: 2008-10-31
forum: General Help
---

### Post by Laibcoms on 2008-10-31
I'm running:
8.10 64-bit
nVIDIA 177 fine.

Only problem is if I use any visual effects setting (Normal or Extra), the Title-Bars of all windows disappear.

Title Bar as in - {icon} {window name} {minimize} {maximize} {close}

I've searched high and low, can't seem to find any related reports, or maybe Im too tired to realize/see similar reports posted :p

Thanks in advance.

---

### Post by flowevd on 2008-10-31
hi

it sounds like you haven't got any window decorations.
check in compiz settings if the 'window decorations' option, under 'effect', is on.

look in the box labelled 'command'.

usually you'll have ```
gtk-window-decorator --replace
```
in there.
or, if you want the fancy stuff,
```
emerald --replace
```

hope this helps.

f

---

### Post by quibbler on 2008-10-31
In compiz manager, make sure window decorations is checked.

Regards quibbler

---

### Post by Laibcoms on 2008-10-31
Ah yes, it was emerald, forgot to install it ^^;;

Thanks thanks!!

---

