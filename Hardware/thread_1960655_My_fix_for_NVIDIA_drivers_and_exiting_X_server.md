---
title: "My fix for NVIDIA drivers and exiting X server"
date: 2012-04-17
forum: Hardware
---

### Post by M1773N5 on 2012-04-17
I'm new to the world of linux and decided to make a dual boot after my intro to UNIX in my IT classes. I installed Kubuntu with no problems (after trying ubuntu and opensuse). My problem was I could not get out of  X server to install the .run. I searched google with many different strings, trying the methods listed to no avail, learned A LOT about linux along the way and finally found a thread that helped me come up with a solution to my problem.

I first reset my root password to gain root access instead of using sudo (DO THIS AT YOUR OWN RISK)

> sudo passwd root
 follow the prompts.

**Write these steps down on paper, you're about to go into command mode.**
> 
ctrl alt f1
log into root
ps -edalf | grep kdm
kill <kdm pid>
sh <nvidia filename>
you may get a warning that a script didn't initialize, install anyways.
go through the install
init 6 after install finishes

If anybody wants to attempt this with sudo, some feedback on your result would be great.

This may not work for everyone, but it worked for me. Just wanted to add my find.:D

---

### Post by oboedad55 on 2012-04-17
> **M1773N5 said:**
> I'm new to the world of linux and decided to make a dual boot after my intro to UNIX in my IT classes. I installed Kubuntu with no problems (after trying ubuntu and opensuse). My problem was I could not get out of  X server to install the .run. I searched google with many different strings, trying the methods listed to no avail, learned A LOT about linux along the way and finally found a thread that helped me come up with a solution to my problem.

I first reset my root password to gain root access instead of using sudo (DO THIS AT YOUR OWN RISK)


 follow the prompts.

**Write these steps down on paper, you're about to go into command mode.**


If anybody wants to attempt this with sudo, some feedback on your result would be great.

This may not work for everyone, but it worked for me. Just wanted to add my find.:D

Thanks for the info. You could, on the other hand, install the current driver through the "additional drivers" app. It will get automagically updated that way too.

---

### Post by M1773N5 on 2012-04-17
I wanted to do it the hard way. :P

---

