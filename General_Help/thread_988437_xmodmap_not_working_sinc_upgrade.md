---
title: "xmodmap not working sinc upgrade"
date: 2008-11-20
forum: General Help
---

### Post by galexcd on 2008-11-20
I pretty much can fix all problems I encounter in ubuntu which is why i haven't registered until today, but I just can't seem to figure this out...

I made this .xmodmap file a while back which switches my Super and Control keys.  I named it .xmodmap and put it in my homefolder.
```
clear control
clear mod4
keycode 115 = Control_L
keycode 37 = Super_L
keycode 116 = Control_R
add control = Control_L Control_R
add mod4 = Super_L
```

It worked fine until I upgraded to ubuntu 8.10 from 7.  Every since upgrading it has managed to do nothing at all.  I tried running xmodmap commands in the terminal, and it does remove the functionality of the control key after typing "clear control", but after I type "control = Control_L Control_R" everything goes back to how it was and the super key is still the super key.  Can anyone help me revise my script to work in ubuntu 8.10?  I've tried virtually everything.

---

### Post by galexcd on 2008-11-20
So I managed to fix it by changing it to this:

```

clear control
clear mod4
add control = Super_L
add mod4 = Control_L Control_R

```

I'm not exactly sure why i don't need the keycode commands anymore, or why in this version the add control and add mod4 values need to be swapped but it seems to work.  Also, this seems to make my super key have control key functionality, but my control key does not become the super key.  It doesn't really matter that much since super isn't used by anything I need but it would be nice if I could set stuff to the control key.

---

