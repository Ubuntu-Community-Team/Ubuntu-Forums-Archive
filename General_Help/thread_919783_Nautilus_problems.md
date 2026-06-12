---
title: "Nautilus problems"
date: 2008-09-14
forum: General Help
---

### Post by Maddoguk2 on 2008-09-14
Can somebody please help me with a problem with Nautilus?
I have recently re-installed Ubuntu on a spare drive. I am also doing some web stuff.
I have LAMP on and it works perfectly. My problem is that when I try to run Nautilus, to copy files to my www folder, I get the following error.


david@david-desktop:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension
Segmentation fault

That is all I get and won't go any further.
I have tried the usual, removing it and re-installing it but still no good.

I am a fairly new user as far as Linux is concerned although I am a network admin (Windows server,Sorry)
:?

---

### Post by aloshbennett on 2008-09-14
I'm not sure what your problem could be, but when using GUIs with root permission, use gksudo instead of sudo
> gksudo nautilus

---

