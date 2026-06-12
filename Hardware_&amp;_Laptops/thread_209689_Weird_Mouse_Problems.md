---
title: "Weird Mouse Problems"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by Chado on 2006-07-05
I've searched and haven't found an answer or anyone else with this problem. Here's the problem:
I'll turn on my Kubuntu machine and I will be able to use it hours on end, non stop. The mouse will function normally. However, when I turn off the monitor and walk away for 10 minutes or so and then come back, the mouse will be able to click on a box (by box I mean window like GAIM or Konqueror), but it will not be able to select anything inside of it. When I try to select something inside of it, the little hand appears and only allows me to move the window. I can't edit anything inside it, can't type in it, etc. I can also click on the K and move in the menus, but not select an item. I restart X and then I can use it for about 5 minutes the first time and then it quits. But at that point at the login screen, my keyboard also freezes. So I can move the mouse, not select anything, and not type. Then it magically goes away. Restart X again and everything is hung.

Sorry if that doesn't flow or make sense. By they way it's just a generic PS/2 wheel mouse.

I did notice though when I went to update a different Kubuntu machine in my house that Adept downloaded an Xorg-Mouse-Input (or something like that) update. I closed it before it finished because I wanted one working machine. I think that this had something to do with it, because it worked just fine until that update came down. Then I had all sorts of problems.

So is there anyway to go back to a previous driver or a way to fix the current one?

Thanks in advance
Chado

---

### Post by ajgreeny on 2006-07-05
Have you tried reinstalling the package *xserver-xorg-input-mouse* again to see what happens.
If you look in synaptic does it mention anything along the bottom bar about broken packages?  If so just go to "Edit/Fix broken packages" and that may do the trick.
Personally I tend to do all my updating with synaptic or aptitude rather than Adept as I find them both far more intuitive to work with.  Whenever I see the "Updates available" icon in my taskbar I click on synaptic, not on the icon and do it that way.  It means I have a better record in the synaptic/history file of what I've done.

---

### Post by Chado on 2006-07-07
OK Gurus, chew on this one. I put in the Live CD and have the same problems. I think that it's a hard drive problem because when I booted up a different time it went to check the filesystem and I got the good old Buffer I/O Error. It's not from a hard shutdown or anything. I did fsck -y and then rebooted. It then checked again and found all the same Logical Blocks bad. Also, I have lost basically all input or when it's not lost, it's too fouled up to use (i.e.: Keys slow to input, keyboard mapped differently). This is using USB and PS/2 keyboards. But when I go to Windows Land, no problems whatsoever.
Any ideas?
Chado

---

