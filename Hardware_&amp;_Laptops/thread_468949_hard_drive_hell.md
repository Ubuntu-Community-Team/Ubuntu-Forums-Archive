---
title: "hard drive hell"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by Spud_Hed on 2007-06-09
i hope someone can help me here before i smash this damn thing into a thousand pieces. for some reason ubuntu automatically (and stupidly) mounts every drive that isnt the main file system as read only, even my usb drives! more annoying is the fact that if i change it to rw instead of ro it just says its unable to mount due to an invalid option, does it not support writing to any drives other than the installed one or something, i even tried setting up another root user account, as the usual root one wont let me in with the pasword that works fine for all other admin things and i cant change it there either, if i dont get it sorted shortly ill be putting xp back on here sharpish, not even vista has managed to p*ss me off this much, 

most annoying of all is i can see no one reason at all that this makes sense for, anyone plugging in a usb drive, be it flash or hard drive is usually likely to be transferring to and from it, unless of course collecting empty drives happens to be your hobby. im really shocked that an os that seems so well put together would have such a nasty issue at all

---

### Post by 444 on 2007-06-09
If the drives are NTFS formatted you need to download ntfs-3g.

---

### Post by Spud_Hed on 2007-06-09
thanks think ive got it sorted now, do i need to remount my drives at every boot?

---

### Post by Spud_Hed on 2007-06-09
ok as expected, the problems dont stop there, i needed to delete some stuff from the drive, but it seems you cant just delete things, you have to send them to the deleted items folder, and once theyre there they dissapear and the space is never freed up on my drive, the trash can or whatever it is is completely empty but my drive is still full. why cant just one thing be simple, just once

---

### Post by 444 on 2007-06-09
Shift-delete.

---

### Post by red_five on 2007-06-10
Do an ls -la on the mounted drive and look for .Trash-username. If you see it, delete it with rm -rf. Whenever you delete something the normal way in Nautilus, on a drive mounted via ntfs-3g, it won't dump it. Instead, it'll put it in that .Trash-username folder.

The Shift-del shortcut will bypass that behavior completely.

---

