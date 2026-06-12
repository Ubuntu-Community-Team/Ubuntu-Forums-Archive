---
title: "[SOLVED] remove password requirement after suspend?"
date: 2008-11-29
forum: General Help
---

### Post by a_toff on 2008-11-29
How do I remove the requirement to enter the user password following Suspend?

I'm running a tablet-pc, and find it pretty annoying to have to always flip the screen back around to get at my keyboard... I'm not overly concerned about the security issue, as I can still lock the screen from the main menu.

thanks!

---

### Post by sdennie on 2008-11-29
Hit Alt-F2 and type gconf-editor.  In gconf-editor, navigate to /apps/gnome-power-manager/lock and uncheck the suspend option (probably hibernate too if you use that).

---

### Post by a_toff on 2008-11-29
thanks!

---

### Post by w-sky on 2012-02-01
> **sdennie said:**
> Hit Alt-F2 and type gconf-editor.  In gconf-editor, navigate to /apps/gnome-power-manager/lock and uncheck the suspend option (probably hibernate too if you use that).

And how do you do this with a more recent Ubuntu and the Unity desktop? This doesn't even work, there is no gconf-editor.

These options should be available in the GUI. I just have been searching on all systems settings, finally came here to the forums (already frustrated) only to see that I would have to resign myself with a regedit-style monster thing with **Gnome** and could not even find a solution for Unity.

It's so much like sh.... M$ Windows: "Click Start, click Run, type Regedit on the Open box, and then click OK. Navigate to the following registry key: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\bla\bla\sucking\bla and change the value of..."

---

