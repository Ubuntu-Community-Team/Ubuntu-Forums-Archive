---
title: "slow computer, boot without x"
date: 2008-07-15
forum: General Help
---

### Post by jonnod on 2008-07-15
hey all, iv installed ubuntu on a very old computer, and i was wondering how i could possibly disable x from the console (because it has a problem with the graphics card and im unable to get to the gnome desktop)

basicly my situation is...

very old computer, installed hardy desktop

realised that its not good enough for desktop edition... need to make it boot without X session 

i can get to recovery console.... and thats about it..

---

### Post by Titan8990 on 2008-07-15
If you don't have any need for the desktop at all you can do:

$sudo apt-get remove --purge ubuntu-desktop

---

### Post by jonnod on 2008-07-15
but wont it then still boot X?? because my prob is that my graphics card only has 2mb of memory so i dont wana be running x at all..i can get into recovery console so i can remove things... should i remove gdm also??

---

### Post by Titan8990 on 2008-07-16
When you remove ubuntu-desktop it should remove gdm as well.

You may have to do this after the uninstall of the desktop:

$sudo apt-get autoremove

---

