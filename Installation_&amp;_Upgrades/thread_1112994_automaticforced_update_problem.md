---
title: "automatic/forced update problem"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by Len Tyree on 2009-04-01
don't know if this belongs here but here goes.

i get the forced update icon on my panel with a list of new updates, as do most of all of us.

i sometimes uncheck an update or two that i do not want, or think i do not need, as i do not use the system they are updating.  
then i update what i want, as usual.

however, the update icon comes back each time i boot up and i look at it to see if anything new has been added, 

the unwanted item is there again with a check mark on it.  so i uncheck the unwanted item again.  

if i do not want a certain update, and i uncheck it, how do i keep the icon from reappearing again and again??

thanks, len tyree.

---

### Post by 3rdalbum on 2009-04-01
Find the package in Synaptic, select it and go to Package > Lock Version. I don't think it will appear in Update Manager anymore, but even if it does there's no way Update Manager will update the package.

---

### Post by Len Tyree on 2009-04-02
thanks 2ndalbum.  SOLVED

went to synaptic, to package, and all items in package were unavailable for change.

so went to synaptic, found main program update was for, marked it for removal (temp), removed same.

lo and behold, update icon disappeared.
len tyree

---

