---
title: "Need help fixing s stupid mistake..."
date: 2008-11-03
forum: General Help
---

### Post by lol@windows on 2008-11-03
Okay, I'm not really new to Ubuntu, but I made a bit of a mistake.  I (stupidly) deleted the entire entry for WIINE, when I shouldn't have, thinking that it would come back when I reinstalled it, though I understand my mistake now.  I'm just trying to rebuild that submenu for WINE from the ground up so I don't have to reinstall Ubuntu totally.

Does anyone know how I should go about doing this?  I can't really find much of anything on my own without it being in the applications menu, and that being what I'm having to rebuild, I need some help.  Anyone want to try and tackle this problem of mine?

Anyway, in summary, I just need to know how to put WINE and everything that goes under it back in my main menu from when I deleted it.  Thanks ^_^

---

### Post by ad_267 on 2008-11-03
Yeah I've done this kind of thing before. The problem is that the menu configuration files say the menu is deleted, and there isn't a graphical way to undelete them.

I think you need to edit the file ~/.config/menus/applications.menu

You can try backing it up and reverting it to some of the menu.undo files. Otherwise you could rename that whole directory to revert back to the default menu, and then redo any changes you've made.

---

### Post by lol@windows on 2008-11-03
I COULD do that... if I had any idea /how/ to do that.  I'm essentially clueless for the following reasons...

1.  I've already done the deleting and have restarted the laptop several times in my many, baffled attempts to correct this, will that be a problem?

2.  I have /no/ idea what to do to edit that file to correct this.  Is there a chance of my getting some sort of an explanation of how to do this?

Thanks for the info so far, just a little more and I'll have essentially undone this.  lol

---

### Post by ad_267 on 2008-11-03
Sorry I had things a bit confused. You should be able to go to ~/.local/share/applications/ and delete the wine .desktop file so that it is no longer deleted from the menu.

Sometimes that doesn't help or there isn't an entry there, I think that might be the case if you delete a category rather than a single entry. You can reconfigure your menu to default by running this in a terminal:
```
mv ~/.config/menus/ ~/.config/menus.backup
killall gnome-panel
```

---

### Post by lol@windows on 2008-11-03
THANK YOU!  That last thing in the terminal did it!  (Jeez... in Windows, I bet I'd have had to completely reformat due to critical error... lol)

---

### Post by ad_267 on 2008-11-03
Whew that's good to hear. Those menu configuration files are confusing!

---

