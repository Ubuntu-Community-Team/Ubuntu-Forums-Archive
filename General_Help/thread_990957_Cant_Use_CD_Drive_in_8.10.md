---
title: "Cant Use CD Drive in 8.10"
date: 2008-11-23
forum: General Help
---

### Post by adrian007 on 2008-11-23
Hi all, 

I upgraded to Ubuntu 8.10 2 days ago. Everything was fine on the first day (CD drive worked) But yesterday i put in a CD and it would simply not mount it and i get the error message

> Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I even tried the Floppy drive (which worked in windows XP) and got same message.

the weird thing is that it worked one day and the next i did not.

Thanks For Any Help.

P.S I don't know if it is related but to use the Floppy dirve i have to use this command: sudo modprobe floppy. I added this kernel module to be automatically launched on start up. Can this cause the problem:confused::confused:

---

### Post by adrian007 on 2008-11-23
No need. I figured it out.

Basically every time the computer comes on the module somehow conflicts with the cd module so i will only need to load the module if i need the floppy drive and unload it after.


SORRY TO BOTHER YOU

---

