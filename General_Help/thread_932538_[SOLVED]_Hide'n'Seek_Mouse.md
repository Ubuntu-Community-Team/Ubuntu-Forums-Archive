---
title: "[SOLVED] Hide'n'Seek Mouse"
date: 2008-09-28
forum: General Help
---

### Post by Qoel on 2008-09-28
When I play Aislerot Solitaire (mouse over a card) or sometimes when I'm surfing with Firefox (mouse over a picture).. my mouse disappears.. Is this right? 

I don't think so.. Does somebody know how to fix it ?
I have a Matrox G200 and I enabled 3D Acceleration (GLXGEARS = 210 fps)
1024x768 @ 85 Hz.
I had no mouse in Wormux too.. Please help ? I don't know what's wrong.

---

### Post by Qoel on 2008-09-28
I solved the problem with the help of [mathman]("http://forum.tuxx-home.at/memberlist.php?mode=viewprofile&u=776") !
> 
Section "Device"
       [...]
	Option 		"HWCursor" 	"False"
       [...]
EndSection


---

### Post by Qoel on 2008-09-29
If you've fixed your issue with the help of this topic.. thank mathman !

---

