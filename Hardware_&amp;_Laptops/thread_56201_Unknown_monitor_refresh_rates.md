---
title: "Unknown monitor refresh rates"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by pompeyjohn on 2005-08-11
Hello all,

I have been given an lcd monitor, but have no idea what its best refresh rates are. Am using figures at the moment that at least provide 1024x768.....but am concerned I might soon smell burning. The monitor is made by a company called Advent.and I have tried googling every code on the damn thing for some more product information - but found nothing. 

So,,,,,,,, was wondering how could I find this information??

Is there a particularly good Live CD from another distro that would work it out?? Or perhaps there is some clever interactive web page....or even some dusty old tech spec page somewhere. I have not found anything yet, and have a blank CD poised for an ISO image....but which one?

cheeers,

john

---

### Post by Juergen on 2005-08-11
If neither monitor nor your graphics-card are older than, say, 7 years ;-) they should be able to communicate via DDC (or whatever that protocol is named)

You can simply omit Hsync and VSync in your xorg.conf.
Reasonable values should then be chosen automatically.

---

### Post by pompeyjohn on 2005-08-12
[QUOTE=Juergen]If neither monitor nor your graphics-card are older than, say, 7 years ;-) they should be able to communicate via DDC (or whatever that protocol is named)

You can simply omit Hsync and VSync in your xorg.conf.
Reasonable values should then be chosen automatically.[/QUOTE]

I dont *think* its that old so am not going to worry about it then....Thanks dude!!  :smile:

---

