---
title: "Problemas whit Ubuntu 9.10"
date: 2009-12-09
forum: Hardware
---

### Post by naxeras on 2009-12-09
Hi,
 
I have a problem to activate Desktop effects in Ubuntu 9.10.
 
I have a intel 855GM card with 3D aceleration enabled but when try activate desktop effects a window with error appeard.
 
If I try activate 3d effects whith **compiz** --**replace **an error whith blacklisted appears.
 
I try to comment  blacklist in compiz cfg file but the desktop freezes.
 
Anyone have the same card whith desktop effects?
 
Please I have desesperate!!! ](*,)
 
Thanks

---

### Post by Fafler on 2009-12-09
The 855GM is very old and slow. Don't expect anything amazing.

I don't know much about compiz, but to check if you have working 3D acceleration, open a terminal and type 

glxinfo | less

Look at the first few lines. You should have one saying

direct rendering: Yes

This means 3D acceleration is enabled and (probably) working.

---

### Post by naxeras on 2009-12-09
Yes, I have 3D aceleration enabled but compiz freezes the system.
 
I need activate compiz because the X-server is slow when move the windows.
 
Please help me [-o<

---

### Post by Fafler on 2009-12-11
Your hardware is slow. I don't think Compiz can make it run faster. Try turning off as many unneded effects as you can.

Other than that, i'm out of ideas.

---

### Post by naxeras on 2009-12-17
Compiz not run onle freezees the system.

---

