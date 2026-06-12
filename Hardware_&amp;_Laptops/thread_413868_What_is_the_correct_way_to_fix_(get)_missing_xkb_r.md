---
title: "What is the correct way to fix (get) missing xkb rules ?"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Rog131 on 2007-04-19
In Feisty i did notice that i have missing keys in the keyboard and Xorg.0.log told:

```
:~$ cat /var/log/Xorg.0.log | grep "(WW)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
...
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
...
```


Also -
```
:~$ setxkbmap -model pc105 -layout fi -variant basic
```
told:

> Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Couldn't find rules file (xorg)

So rules are missing ?

In the dapper usr/X11R6/lib/X11/:

fonts  icons  locale  xkb


But in the feisty usr/X11R6/lib/X11/ only have

fonts  icons


Quick and dirty fix: Copy dirs from dapper to feisty. Seems to work.

But what is the right way (tm) ?

---

