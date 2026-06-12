---
title: "Remapping Right Alt-key on MacBook Pro"
date: 2010-02-05
forum: Hardware
---

### Post by MeMooMeM on 2010-02-05
Hi everyone,

I am trying to remap the right ALT key to function as forward delete on MacBookPro. 

Normally, forward delete requires fn+delete combination. To capture the keycode, I used xev, which returned:

```
119 for fn+delete
108 for right ALT
```

however, when I assign 119 to 108 by adding

```
keycode 108 = 119
```

into .Xmodmap, I get 'w' instead???! 

Any ideas? Thanks a lot! :)

---

### Post by MeMooMeM on 2010-02-11
Nothing?

---

### Post by MeMooMeM on 2010-06-12
Found it:

(1) edit (or create) ~/.Xmodmap
(2) add the line:
    keycode 108 = Delete
(3) After you reboot, a dialog box will ask you if you want to load it. Just select .Xmodmap and load and make sure "do not show this again" box is checked.

Enjoy :)

---

