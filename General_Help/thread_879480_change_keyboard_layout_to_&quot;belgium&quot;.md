---
title: "change keyboard layout to &quot;belgium&quot;"
date: 2008-08-04
forum: General Help
---

### Post by spwn on 2008-08-04
Hey, i saw [this topic]("http://ubuntuforums.org/showthread.php?t=290021") and i figured, that it was easy, but i am not going to take any more chances then nessecary.

So maybe someone could help me as in what i should put in "xorg.conf" on that line, to add a BELGIAN keyboard layout...

You see normally i would be happy with french (since they are azerty).
However, there kind of weird...

this is when i type my first 6 letters: azerty
but this is what i type my special chars: &é"'(-è_çàà)

For those who know azerty, here in belgium thats not the right special chars. And its kind of searching for the @ always and others too.. :)

So it would be nice if i can get it into the list of "Keyboard Layout Switcher" :)

---

### Post by mali2297 on 2008-08-04
There is an old doc here:
[https://help.ubuntu.com/xubuntu/desktopguide/C/switch-keyboard-layout.html](https://help.ubuntu.com/xubuntu/desktopguide/C/switch-keyboard-layout.html)

In your case, I think that you want a line like this (in the keyboard section):
```

Option          "XkbLayout"     "fr,be"

```

---

### Post by todak on 2008-08-04
System> Preferences> Keyboard gets you the keyboard layout GUI.

---

### Post by Archimedes0212 on 2008-08-04
to add onto Mali's post (2 above mine) you may also have to alter the variant option as well.  Not sure what it will be in your case, but it just needs some playing around.

good luck

---

