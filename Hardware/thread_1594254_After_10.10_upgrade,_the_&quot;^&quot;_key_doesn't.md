---
title: "After 10.10 upgrade, the &quot;^&quot; key doesn't work anymore"
date: 2010-10-12
forum: Hardware
---

### Post by tomgie on 2010-10-12
hi,

yesterday I upgraded from Kubuntu 10.04 to 10.10 and since then the "^" symbol doesn't work anymore. The key itself does work, e.g., I get the symbol in a browser but not in the terminal or in an editor. The key also works with SHIFT (which produces that small circle).

I'm running 10.10 on a Dell Inspiron 6400 with German keyboard layout. I even chose "Dell Inspiron 6xxx series keyboard". But no change.

I'm very grateful for any hints. I desparately need that key for superscripts in Latex.

Many thanks,

Tom

---

### Post by Zorael on 2010-10-12
Try the following, then logout and back in.
```
$ im-switch -s none
```
You may also need to completely remove ibus if KDE programs refuse to stop using it.
```
$ sudo aptitude purge ibus libibus2
```

---

### Post by tomgie on 2010-10-12
hi,

many thanks, but unfortunately, it doesn't work. i tried the first command several times and the second once, and i also completely rebooted every time. no change.

i discovered a second symbol that doesn't work: "´".
as with the other one, if i use SHIFT, the correct symbol for that key appears, and as before, it also works in a browser.

cheers,

tom

---

### Post by tomgie on 2010-10-12
Update: everything works fine in Mathematica, OpenOffice, Chromium

doesn't work in Terminal, Kile, Lyx

tom

---

### Post by Zorael on 2010-10-12
Interesting.

Try default-xim, then.
```
$ im-switch -s default-xim
```
And as before, you'd have to log out and back in for it to take effect.

**edit**: And to clarify things; do you want the key to enter ^ immediately upon pressing it? Because it "should" be a dead key, where you have to press ^ and then space for the symbol to appear. That way you can type international characters, like ô by pressing ^ and then o.

Conversely, if it becomes ^ immediately in some programs (Chromium et al), those programs are exhibiting the "wrong" behavior.

---

### Post by tomgie on 2010-10-12
wow, now it works!

many thanks!

thomas

(the ^ doesn't come immediately, only when i press the key a second time, as it should probably.)

---

