---
title: "[SOLVED] trash bin icon is missing from my desktop?"
date: 2008-07-27
forum: General Help
---

### Post by cowboyup6983 on 2008-07-27
hi all. i'm having a little problem i hope i can get some help with. the trash bin icon thats usually located at the bottom right of the screen disappeared today. i think i accidently choose to remove from panel instead of empty trash. 

please let me know what i can do. thank you so much 2 all.

---

### Post by jonian_g on 2008-07-27
Right click on the panel and choose "Add to panel". On the window that comes up find the trash bin, select it and click the add button.

It will appear on your panel. To move it and place it where you want, right click on the trash bin icon and choose move.

---

### Post by coffeecat on 2008-07-27
Do you want the trash on the desktop or on the lower panel?

If desktop: open a terminal or press alt-F2 and type 'gconf-editor' (no quotes) and press return. In the Configuration Editor window, navigate to apps > nautilus > desktop and tick trash_icon_visible.

If panel: right-click on panel, select 'Add to Panel' and choose Trash. It's actually called 'Deleted Items' on my install, but I don't know whether the name varies according to region. My system is set for English (UK) - perhaps it's different for other variants of English. I don't know.

---

### Post by cowboyup6983 on 2008-07-27
> **jonian_g said:**
> Right click on the panel and choose "Add to panel". On the window that comes up find the trash bin, select it and click the add button.

It will appear on your panel. To move it and place it where you want, right click on the trash bin icon and choose move.

again, thanks for such a quick response. it work perfectly as stated, even added a few other items, i didnt know about. do you know if ubuntu has a "dock" kinda like MAC OS X. it also looked kinda cool to me.

---

### Post by jonian_g on 2008-07-27
Yep. Go to add/remove and install Avant Window Navigator. It's the best in my opinion. You must have compiz enabled for it to work.

---

### Post by stepbystep on 2008-10-02
thanks for that

---

### Post by retro_killa on 2010-03-02
> **coffeecat said:**
> Do you want the trash on the desktop or on the lower panel?

If desktop: open a terminal or press alt-F2 and type 'gconf-editor' (no quotes) and press return. In the Configuration Editor window, navigate to apps > nautilus > desktop and tick trash_icon_visible.

If panel: right-click on panel, select 'Add to Panel' and choose Trash. It's actually called 'Deleted Items' on my install, but I don't know whether the name varies according to region. My system is set for English (UK) - perhaps it's different for other variants of English. I don't know.

Thanks for this

---

### Post by xiongnu on 2010-11-19
> **coffeecat said:**
> Do you want the trash on the desktop or on the lower panel?

If desktop: open a terminal or press alt-F2 and type 'gconf-editor' (no quotes) and press return. In the Configuration Editor window, navigate to apps > nautilus > desktop and tick trash_icon_visible.



same problem here - missing trash can on desktop. 


and i did above. but the trash icon still doesn't show up on desktop.  any ideas?

---

