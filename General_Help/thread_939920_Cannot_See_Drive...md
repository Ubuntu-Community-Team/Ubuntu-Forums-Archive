---
title: "Cannot See Drive.."
date: 2008-10-06
forum: General Help
---

### Post by sunny_pirate on 2008-10-06
I have Windows Vista installed on C: of my computer. I installed Ubuntu 8.04 in Windows on D: with 5gb space using wubi-installer.

The problem is that I cannot see the D: contents in Ubuntu. Also, I can see C: Contents but not My documents and desktop?? 

Another Question: Is there any way by which I can increase the alloted 5gb space without reinstalling Ubuntu?

---

### Post by johnphilips on 2008-10-06
Hi sunny_pirate.
Even I faced the same problem. Vista is useless. I think visit on the Microsoft forum.

John Philips
[Search engine]("http://www.yahoo.com")

---

### Post by Aximilli on 2008-10-06
I'm not sure if this is helpful, but Ubuntu won't see where you installed it as the D: drive, it will see that volume as File System

And My docs will most likely be in \media\hda(whatever)\Documents and Settings\YourUSerName\UserNames Documents

---

### Post by Tethylis on 2008-10-06
I think Aximilli is correct, because linux can browse the windows NTFS file system and windows cannot browse the JFS1 linux file system.

---

### Post by sunny_pirate on 2008-10-08
I found the Solution.. It is in /host/

---

