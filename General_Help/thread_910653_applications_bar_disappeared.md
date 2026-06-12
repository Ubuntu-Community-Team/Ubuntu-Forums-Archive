---
title: "applications bar disappeared"
date: 2008-09-04
forum: General Help
---

### Post by harveybosco on 2008-09-04
I lost the task bar!!...am only seeing screen icons..so that means i have to unplug power cable to shut down computer,since i can't find the application taskbar with shutdown buttons.
how can i get the taskbar back?!..running xubuntu

thanks for any reply

---

### Post by colinlbrown on 2008-09-04
if it makes you feel any better i have just done exactly the same and also wait for any answers you have.

i only got 3 items on screen and can't get at anything!!

---

### Post by kk0sse54 on 2008-09-04
Try restarting your panel by pressing alt + f2 and typing in xfce4-panel in order to start your xfce panel(Forgive me if that's not the exact command I haven't used xfce in a while)

Instead of pulling out your power cable though try pressing ctrl + alt + backspace in order to restart X and login again. Once you get to the login screen you can also choose to shutdown instead otherwise if you don't want to restart x press alt + f2 and type gnome-terminal. In the terminal type ```
sudo shutdown -h now
``` in order to shut your computer down ,replace the h with r in order to have it reboot instead.

---

### Post by colinlbrown on 2008-09-04
your certainly on the right lines but code isnt right as file isn't found.Is there a way to return to factory settings as i have nothing to lose by doing that.

---

### Post by stoneage on 2008-09-04
Try 'Press Alt+F2 and input command gconf-editor to open Configuration Editor, go to app > panel > general and open toplevel_id_list , then you should be able to add a panel there - "top_panel_screen0" or "bottom_panel_screen0"'


EDIT - Oh, are you on Xubuntu; this is for Ubuntu, but should be the same.

---

### Post by stoneage on 2008-09-04
.....Or simply type "gnome-panel" in the Terminal....?

---

### Post by kk0sse54 on 2008-09-04
> **stoneage said:**
> .....Or simply type "gnome-panel" in the Terminal....?

That starts a the gnome panel not the xfce panel. To the Op try this out [http://wiki.xfce.org/faq](http://wiki.xfce.org/faq) towards the bottom of the page they mention a disappeared panel

---

### Post by colinlbrown on 2008-09-04
Thanks for that but i still have the problem of no applications (or any other) tab showing.
It shows what i have open but i cannot get at any other programmes other than are showing on my descktop, which is only 3!!

---

### Post by kk0sse54 on 2008-09-04
> **colinlbrown said:**
> Thanks for that but i still have the problem of no applications (or any other) tab showing.
It shows what i have open but i cannot get at any other programmes other than are showing on my descktop, which is only 3!!

Can you please clarify? So you do have a panel present but just not your normal fefatures on it? If so right click the panel and click Add new item from there you can add more stuff to your panel.

---

### Post by stoneage on 2008-09-04
> **stoneage said:**
> .....Or simply type "gnome-panel" in the Terminal....?

..yeah, sorry about that.

You could try a different theme, but I don't know what happens when you revert to the one you were using.

---

### Post by harveybosco on 2008-09-09
thank you very much all,
pressing alt + f2 and typing in xfce4-panel seems to have fixed the missing panel problem for me.
I also had to click ” Save session automatically on logout” somewhere along the line...

anyhow,it works...i am happy
love linux...don't know too much about it yet...have tried different distributions,but seem to prefer xfce desktop...seems to be way faster than other desktop sessions

thanks again,[http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

---

