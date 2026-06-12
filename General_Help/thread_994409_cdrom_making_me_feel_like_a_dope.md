---
title: "cdrom making me feel like a dope"
date: 2008-11-26
forum: General Help
---

### Post by Toriam on 2008-11-26
I cant get a cd out. Ive sudo eject'ed it, clicked the orange eject  icon in a window, sudo unmount'ed it. rrr. i just installed ibex and this is the first time ive tried to get a cd out. it does nothing.

---

### Post by amauk on 2008-11-26
most cd drives have a pin hole to manually open the tray
shut down the machine and use a paperclip to get the cd out

---

### Post by Toriam on 2008-11-26
No luck with the little hole. I noticed that while the computer says it sees the CD in the drive, and can read it, mount it and unmount it, it refuses to eject it. I got an error about ioctl being off, umm, permissions?
Nope, it said:
toriam@toriam-laptop:~$ sudo eject -f
eject: unable to eject, last error: Inappropriate ioctl for device
 When I wrote permissions, it made me think of users and groups, so i let my user do everything, and still got that message. And now it says it can't be mounted.

---

### Post by Toriam on 2008-11-27
Bump!

---

### Post by CatKiller on 2008-11-28
> **Toriam said:**
> No luck with the little hole.

What happens if you restart the machine and press the eject button early in the boot process?

---

### Post by ideewoww on 2008-11-28
[img]http://www.ideewomen.com/index.jpg[/img][http://www.ideejewelry.com](http://www.ideejewelry.com/)

---

### Post by Toriam on 2008-11-28
Nothing. I can hear the disc spinning up, and the PC sees it, and the icon for it disappears soon after I hit eject. But no disc comes out. Could my drive possibly simply be stuck? I've gently ran my fingernail in the crack between the edge of the drive door and the machine, nothing seems wrong. Recently while i was inserting a disc the tray went in funny, the power  cord is right by it and  was turned funny, so if its that this may have caused it....

---

### Post by CatKiller on 2008-11-29
> **Toriam said:**
> Nothing. I can hear the disc spinning up, and the PC sees it, and the icon for it disappears soon after I hit eject. But no disc comes out. Could my drive possibly simply be stuck? I've gently ran my fingernail in the crack between the edge of the drive door and the machine, nothing seems wrong. Recently while i was inserting a disc the tray went in funny, the power  cord is right by it and  was turned funny, so if its that this may have caused it....

I meant during the memory check, before GRUB has loaded. No icons at that point :)

It is possible that the tray has jammed. The hole that amauk mentioned is a purely mechanical method to eject the tray. You need to push your paper clip in quite a long way.

---

### Post by editrix on 2008-11-30
Sometimes this works for me:
command 1: sudo fuser -k /media/cdrom0 (or whatever your cd reader is called)
command 2: eject

---

