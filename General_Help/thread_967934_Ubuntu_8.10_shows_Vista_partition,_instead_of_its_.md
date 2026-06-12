---
title: "Ubuntu 8.10 shows Vista partition, instead of its own"
date: 2008-11-02
forum: General Help
---

### Post by SpyderX on 2008-11-02
Hi, I orginally had vista on a 499gb partition, and i had two other  partitions that were blank: 59gb and a 39gb partition.I then installed ubuntu into the 39gb partition, did not use any swap space, so just installed onto the 39gb partition. Using the gnome bootloader I logged onto ubuntu and I see that a 524.3gb HD shows up and all of my vista data inside of it ("program files" folder, etc). How is this possible, it want to install everything ubuntu on the ububtu partition (the 39gb one), why isnt that partition showing?

---

### Post by Titan8990 on 2008-11-02
It actually is showing. "Filesystem" would be your Ubuntu partition. It starts at / which would be the equivalent of C:\ in Windows. Most of the time you will store most of your files in your home folder, Places -> Home or /home/YOURUSERNAME.

See this for more info: [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)


When drives other partitions are used they are "mounted". This gives them a location in the filesystem usually in the /media directory. Drives/partitions that are mounted in the /media directory appear on your desktop.

---

