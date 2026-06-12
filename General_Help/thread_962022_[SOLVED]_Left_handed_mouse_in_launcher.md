---
title: "[SOLVED] Left handed mouse in launcher"
date: 2008-10-28
forum: General Help
---

### Post by R2D2! on 2008-10-28
([http://ubuntuforums.org/showthread.php?t=940986](http://ubuntuforums.org/showthread.php?t=940986))
Is there any command in gnome-mouse-properties that could switch between left- and right-handed mode?

I wanna create a launcher that just switches the mouse; because many people use my computer, and they are all right-handed (weird, isn't it?).

—Ilhu&#305;temoc &#948;

---

### Post by R2D2! on 2008-11-23
As nobody seems to answer, I w&#305;ll g&#305;ve the solut&#305;on I've found.
For a left-handed mouse:
```
xmodmap -e 'pointer = 3 2 1' & synclient TapButton1=3 & synclient RBCornerButton=1
```
For a r&#305;ght-handed mouse:
```
xmodmap -e 'pointer = 1 2 3' & synclient TapButton1=1 & synclient RBCornerButton=3
```

—Ilhu&#305;temoc &#948;

---

