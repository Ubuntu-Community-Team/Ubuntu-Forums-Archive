---
title: "Uh oh... I made my resolution tiny by mistake.."
date: 2008-11-04
forum: General Help
---

### Post by TheHerb on 2008-11-04
I accidently made my resolution like 300x300 and now i can't even change it back because i can't get to the part of the screen resolution that has the drop down... is there a command i can enter or something?

---

### Post by mikewhatever on 2008-11-04
You could try <sudo dpkg-reconfigure -phigh xserver-xorg>.

---

### Post by TheHerb on 2008-11-04
didn't seem to do anything :P

---

### Post by alenis on 2008-11-04
With Intrepid you can start in recovery mode and then you have an option to reconfigure the X server

---

### Post by TheHerb on 2008-11-04
> **alenis said:**
> With Intrepid you can start in recovery mode and then you have an option to reconfigure the X server

How do i go about doing this?

---

### Post by alenis on 2008-11-04
When Grub starts you should see something like "press ESC to enter menu". Press ESC and the recovery option should be the second in the list. I'm sorry I can't restart my computer right now, but I hope this information is enough.

---

### Post by geirha on 2008-11-04
Perhaps try this first. After logging in to your currently unusable session, hit Ctrl+Alt+F1 to get to a console terminal. Log in, and run this:
```
DISPLAY=:0 xrandr
``` It should list the possible video-modes you can set. Hit the up-arrow key to get the previous command typed in again, and add -s resolution to it. For example
```
DISPLAY=:0 xrandr -s 1024x768
```

Hit Ctrl+Alt+F7 to get back to the graphical session.

---

### Post by TheHerb on 2008-11-04
> **geirha said:**
> Perhaps try this first. After logging in to your currently unusable session, hit Ctrl+Alt+F1 to get to a console terminal. Log in, and run this:
```
DISPLAY=:0 xrandr
``` It should list the possible video-modes you can set. Hit the up-arrow key to get the previous command typed in again, and add -s resolution to it. For example
```
DISPLAY=:0 xrandr -s 1024x768
```

Hit Ctrl+Alt+F7 to get back to the graphical session.

that gives me an error -.- lol

---

### Post by geirha on 2008-11-04
Which of the commands give an error, and what does the error message say?

---

