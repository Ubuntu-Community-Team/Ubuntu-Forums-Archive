---
title: "Title bar icons inverted"
date: 2008-11-14
forum: General Help
---

### Post by svanpoeck on 2008-11-14
Hi,

After installing the compiz-fusion/awn theme Mac4Lin, the icons in the titlebar of all apps have reverted: the close/minimize/maximize icons are on the left - screenshot attached.

I've been through some of the conf files I could think of but did not find the responsible setting.

I've also deactivated/reactivated compiz-fusion to no avail.

Anyone has a clue ?

Thanks,
Steven

---

### Post by svanpoeck on 2008-11-14
Hi again,

Came to think of it: this theme had an installer script (theme URL [http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/)).

So I opened it and found this line:
```
gconftool-2 --set /apps/metacity/general/button_layout --type string "close,minimize,maximize:menu"
```

I solved my issue using this line:
```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
```

And now everything is back to normal :)

Hope this may help someone,
Steven

---

### Post by jokoon on 2009-01-09
Doesn't work for me :-(

---

