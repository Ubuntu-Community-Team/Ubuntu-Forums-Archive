---
title: "Unable to write on a Memory Card SD"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by Turtle.net on 2006-11-28
I have a eMachine and everything is working out of the box. I have a multicard reader, and when I insert a memory card SD, the card automount and I'm able to navigate into the folders, view the files and even open them (pics or songs for instance).
My problem is when I copy a file on it. Everything seems to work perfectly  (the files appear into the right folder) but when I unmount the card and remount it the copied files seems to have disappeared ... ](*,)

Any idea ?

---Edit
Gparted is unable to recognise the filesystem.
I use this card on my palm. Is it possible to have a problem of filesystem due to palm ?

---

### Post by GnarusLeo on 2007-07-17
I have exacly the same problem. Any sollution to this?

---

### Post by dabl on 2007-07-17
Yep.

You need to remember that Linux uses "cached writes".  The files that you THINK you saved on the sd card, and which appear to be there when you view it after "saving" them, are in fact in a cache awaiting their turn to be dealt with.  So when you yank your sd card out of the reader, you have beat your computer out of the chance to write the data to the card.

Instead of just pulling it out, use "Safely Remove" or "Eject" of "Unmount" -- whatever right-clicking on the device icon offers you.  This will let your system flush the cache to the device, then it will tell you "OK to remove", and then you'll have your files plus the filesystem on the device won't be screwed up when you try it in Windows.  :)

---

