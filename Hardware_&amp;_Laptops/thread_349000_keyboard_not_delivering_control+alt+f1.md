---
title: "keyboard not delivering control+alt+f1"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by Daveth on 2007-01-29
Hi.
A recent excursion with "envy" led me, through lack of experience and a small amount of mild panic,  to have to reconfigure the xorg.conf through the manual route. I answered the questions as best as I could, but now find my keyboard will not execute control+alt+f1 to get to the terminal to re-try envy. Nothing happens with this keystroke combo. Stupidly I copied over the conf.bak file. 

It is a generic keyboard, but all the generic options do not seem to get me anywhere.
It is possible to force dapper to re-find this keyboard and put it back the way it was? Is it as simple as un-plugging it?

---

### Post by Paerez on 2007-01-29
you can boot into a terminal by booting the Ubuntu Recovery option at boot. Wow I just said boot three times in one sentence.

---

### Post by Daveth on 2007-02-03
Thanks but this is worse than I thought. All the upper key sections- so the @ key, tilde and others- seem transposed along the keyboard. The @ is gained by hitting the double quotes key!
All the xorg.conf backups are after the problem, so I cannot return to the original. If I try this, I get:

```
xprop -root | grep XKB
_XKB_RULES_NAMES(STRING) = "base", "pc106", "us", "", ""
_XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""

```

Do they have to match? The back of the keyboard has UK/Euro as the area designation.

Anyone got any ideas?

---

### Post by Paerez on 2007-02-03
ok, once you get into the terminal, type:
```
sudo dpkg-reconfigure xserver-xorg
```
and when it asks you about your keyboard, put in the UK one.

---

### Post by Daveth on 2007-02-04
al better now. Thanks very much. :)

---

