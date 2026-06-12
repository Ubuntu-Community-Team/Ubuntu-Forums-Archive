---
title: "Help with Partitions!!"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by jglayden on 2009-07-19
I just installed Ubuntu on a Dell laptop with Vista Business already installed. I was going to originally install it as a Live CD but, it asked me if I wanted to install as a dual boot? I said, sure. It went into the installation process and because when I was in a rush, I didn't realize that it wanted to create another partition on my hard drive. Again, no problem. I then started playing around with it and was amazed how cool this new OS was. The update manager started and told me that there were new updates. I clicked on the "OK" button to download the new updates and it told me that there wasn't enough space! I have a 109 GB HDD and have 57 GB unused? I then realized that Ubuntu made a 2.3 GB partition on that drive. The program uses almost all that space. I tried to download Gparted but, still not enough. I don't have enough space even after uninstalling Open Office and other non-essential programs. 
What should I do? I don't want to uninstall it. I was told that I can run Vista CD and do a recovery. Is there an easier way to do this? All I really need is more space on my Ubuntu partition. Do I have to uninstall and reinstall? Please Help!!:confused:
Thank you

---

### Post by Post Monkeh on 2009-07-19
reload your installation cd, go to system - admin - partition editor. edit the windows partition and reduce its size. then edit the ubuntu partition and increase it to fill the space. it'll take a while, because all your data will be moved to the start of the newly enlarged partition.

---

### Post by merlinus on 2009-07-19
As all-too-many threads and user experiences have indicated, you need to use vista's disk management tool to shrink or resize its partition, whilst defragging several times beforehand.

Anything else is an invitation to disaster.

gparted works well with xp or 2000, but definitely not with vista or 7.

---

### Post by Post Monkeh on 2009-07-19
> **merlinus said:**
> As all-too-many threads and user experiences have indicated, you need to use vista's disk management tool to shrink or resize its partition, whilst defragging several times beforehand.

Anything else is an invitation to disaster.

gparted works well with xp or 2000, but definitely not with vista or 7.

really? i installed ubuntu beside vista with no problem. gues i was just lucky.

---

### Post by merlinus on 2009-07-19
I never said that you could not install ubuntu side-by-side with vista.  I wrote about how to resize vista's partition to make room for it.

Probably we only get the disaster scenarios reported here.   :)

And, as always, YMMV...

---

### Post by Post Monkeh on 2009-07-19
i mean i just used the standard ubuntu installer to resize the partition. i shrunk it by quite a bit with gparted, and it still booted with no problems. having done a bit of research, i see i was very lucky.

---

