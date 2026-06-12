---
title: "How to fix icons position in status bar?"
date: 2008-11-24
forum: General Help
---

### Post by abcuser on 2008-11-24
Hi,
in Ubuntu 8.10 at the top-right site of window there is "status bar". I can change the position of icons, but every time system reboots or logs off this icon positions changes. This makes me "mad"... :(  Is there any way I could fix the position of icons in status bar?

Please see attached picture. I would like "me" and shutdown icon to always be at top-right position. 
Regards,
Abcuser

---

### Post by EnGorDiaz on 2008-11-24
> **abcuser said:**
> Hi,
in Ubuntu 8.10 at the top-right site of window there is "status bar". I can change the position of icons, but every time system reboots or logs off this icon positions changes. This makes me "mad"... :(  Is there any way I could fix the position of icons in status bar?

Please see attached picture. I would like "me" and shutdown icon to always be at top-right position. 
Regards,
Abcuser

right click make new panel delete the old panel you have there and then right click add to panel and put the icons on you want

---

### Post by JacksonJimbo on 2008-11-24
There is a chech button if you right click on any icon. You have to mark this. Sometimes it doesn't help. If so then try to reconf your gnome-panel as sudo, but first you have to rearrange your icons and then type in the console

```
dpkg-reconfigure gnome-panel
```

This should fix it. I had this problem also and now it works.

Good luck!

---

### Post by abcuser on 2008-11-24
@JacksonJimbo, that solved my problem for a temporally. I have logouted and it worked fine, reboot and worked fine, but after shutdown the icons order is corrupted again. See attachment. I want "me"&shutdown menu always at top-right.

@EnGorDiaz, I can't delete the panel, because all icons I have on top panel - I have removed bottom panel, because it just occupies too much of the screen.

---

### Post by Matthewthegreat on 2008-11-24
You probably tried this but does right clicking then lock to panel work?

---

### Post by abcuser on 2008-11-24
Hi,
I did:
1. unlocked icons,
2. moved them to position I like to have it,
3. executed command: sudo dpkg-reconfigure gnome-panel
4. locked icons,
5. halted the system and then boot it again and icons order mess reappeared.
Any idea?
Regards

---

