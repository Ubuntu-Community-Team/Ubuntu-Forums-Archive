---
title: "opl3 - old laptop ubuntu 5 no sound"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by Ramses100 on 2005-05-13
Hi,

I just installed ubuntu 5 onto my old laptop (266mmx system) and everything works fine (after 3 hours waiting) except for the sound.

I know that the soundcard is a yamaha opl3, but I have no idea as how to get it to work, as I am a beginner with linux/ubuntu.

Can anyone help me?

Greetz,

Ramses

---

### Post by az on 2005-05-13
try opl3sa or opl3sa2

sudo modprobe opl3sa2

---

### Post by Ramses100 on 2005-05-14
Well, i found a post somewhere, and i copied what it said in there and now sound is working, but i am still having issues.

If I select my soundcard for soundevents, it isnt available for other sound related progs. Like totempole mediaplayer, it says the soundcard is occupied. If I turn off sound events, I can use it for totempole (play cd's).

Furthermore, when I login as a user different then the administrator one, it says access to the sound device is denied or something.

Any thoughts please?

Greetz,

Ramses

---

