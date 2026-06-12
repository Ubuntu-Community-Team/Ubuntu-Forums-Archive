---
title: "Upgrade Manager Problems"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by bluzit on 2009-10-30
I'm trying to install the new Opera version with a deb file but it stops and says that I cannot run two update services at once. How do I close Synaptic? I'm using Ubuntu 9.10. Thanks
 Everything else seems to work fine.:confused:

---

### Post by grandtoubab on 2009-10-30
**ps -edf | grep synaptic**

and kill the process

---

### Post by bashphoenux on 2009-10-30
if you have stopped the synaptic in the middle of something then you would have to delete 'lock' file

---

### Post by bluzit on 2009-10-30
My package upgrade manager fails also, can't download or install updates. Oh boy.:(

---

### Post by bluzit on 2009-10-30
I can't make any progress with this, I guess I will have to start with a clean install of 9.10. Without update capability the system is useless to me. Thanks:(  Found a post with a fix that worked. I entered two sudo commands into a terminal and all is well again. Thanks all :)

---

