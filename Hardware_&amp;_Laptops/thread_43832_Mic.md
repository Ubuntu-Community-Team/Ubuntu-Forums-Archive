---
title: "Mic"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by Chen_Zhen on 2005-06-23
Hi everybody, it's very strange but I don't manage to figure out why my microphone isn't working. I checked my alsamixer settings and volumes should be alright. I don't know if there is a connection but multiple sounds also doesn't work on my ubuntu.Can anyone give me some tip? Thanks

---

### Post by Wardhog on 2005-06-26
[QUOTE=Chen_Zhen]Hi everybody, it's very strange but I don't manage to figure out why my microphone isn't working. I checked my alsamixer settings and volumes should be alright. I don't know if there is a connection but multiple sounds also doesn't work on my ubuntu.Can anyone give me some tip? Thanks[/QUOTE]

I plugged in my microphone yesterday and discovered that it didn't work.  However, killing the ESD process fixed things for me.

$killall esd

Now happily Skypeing along.  Turns out my microphone did work, it was just ESD getting in the way.

---

