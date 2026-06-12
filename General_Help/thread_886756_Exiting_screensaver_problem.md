---
title: "Exiting screensaver problem"
date: 2008-08-11
forum: General Help
---

### Post by Archimedes0212 on 2008-08-11
Hey all -

I've got this problem with my screensaver (I guess).  After x amount of time my screensaver will kick in.  When I shake my mouse or something to leave the screensaver and be prompted for my password, ubuntu freezes.  The only way out of it is for me to restart X, which is a terrible fix because I lose whatever I had opened before my screensaver turned on.  

I'm running Hardy.

Any ideas??

Thanks in advance

---

### Post by Archimedes0212 on 2008-08-11
bump

---

### Post by gldblade on 2008-08-13
Many of the 3D screensavers seem to cause freezing problems on a bunch of computers.  Try switching to a different screensaver.

Note: If you try to switch to a different screensaver and the screensaver configuration application freezes, then it's definitely the screensaver's fault.  How can you switch to a different screensaver if the configuration application freezes?  Open up gconf-editor from a terminal, go to /apps/gnome-screensaver, and clear the key "themes".

---

### Post by Archimedes0212 on 2008-08-13
I'll have to give this a shot when I get back to my linux system

---

### Post by Archimedes0212 on 2008-08-15
yeah, i tried switching to a non-3D screensaver and it still froze.  

Any ideas on fixing this problem??

---

### Post by SpaceMaster on 2008-08-15
do you have the restricted modules for your graphics card installed?

---

### Post by Archimedes0212 on 2008-08-15
where can I see if I do?



(I've got ATI graphics on an IBM Thinkpad T60)

---

### Post by SpaceMaster on 2008-08-18
Easiest way to check is to go to:
System -> Administration -> Hardware Drivers
That will show all available restricted drivers.  What you'd be looking for is to see if "ATI accelerated graphics driver" (or something very similar thereto) is marked as "[COLOR="Lime"]**In use**[/COLOR]"

---

### Post by Archimedes0212 on 2008-09-13
yeah, it's marked as in use but still no luck

---

### Post by Archimedes0212 on 2008-09-14
I've gotten picture screensavers to work,  but the 3D ones still don't.  Any ideas?   Thanks

---

