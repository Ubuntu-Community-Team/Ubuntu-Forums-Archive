---
title: "I need help with Grub error 17!"
date: 2008-06-28
forum: Hardware
---

### Post by jme371 on 2008-06-28
I actually had SuSE but this site seems to have better advice and this is a general question anyway. Basically I want to remove Linex from my laptop and only have Windows XP for the space since I play a lot of games and really don't have a use for Linex, so I reformatted the swap drive partition of SuSE but the left the main partition for a little while to see if there were any other files I would want off of it. I turned off my computer, and now Grub comes up with error 17. I'm guessing this is because it is trying to read the linex partition but that partition can't work. I want to simply boot straight to Windows but Grub gives me no options at all. So, what should I do to fix this? I think one possibility may be to reload Grub, does anyone know if this would work and does anyone have a link to a good tutorial on how to setup Grub? Thanks for any help given!

---

### Post by AlexBellisBrown on 2008-06-28
I recommend you try this, should sort GRUB, providing you are able to burn a CD with another computer. If not, i think youll need the Ubuntu Live CD and edit the Boot from Terminal.:)

[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

---

### Post by AlexBellisBrown on 2008-06-28
OR!!! You use the Windows Rescue CD, if youre planning on abandoning Linux... Hope this helps.

---

### Post by jme371 on 2008-06-28
Thanks for the help and I was able to fix the problem using the Windows recovery CD and the fixmbr command so I'm good. Thanks again.

---

