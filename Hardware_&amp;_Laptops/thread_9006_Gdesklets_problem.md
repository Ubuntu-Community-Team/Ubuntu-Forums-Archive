---
title: "Gdesklets problem"
date: 2004-12-23
forum: Hardware &amp; Laptops
---

### Post by lyahgelo on 2004-12-23
I've a problem with gdesklets.
When I start desklets my CPU is occuped 100%.
Is a common problem?
 ](*,)  ](*,)

---

### Post by Maxobelix on 2004-12-30
I've got same problem before...
   
   Try this to fix that issue :
   
   First unload gdesklet (kill it)
   Then, before loading gdesklets server,  type this on a term.
   
   >  
   bash-2.05b $ gdesklets /usr/share/gdesklets/Displays/disk/disk.display
     
 I think this updates (or resets) Gdesklets conf. files with good parameters (?)
 
 Then load the gdesklets server via the gnome menu (applications -> launch).
   
   Finally, launch all displays you want...

---

