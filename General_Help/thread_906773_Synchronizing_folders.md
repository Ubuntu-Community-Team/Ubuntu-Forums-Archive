---
title: "Synchronizing folders"
date: 2008-08-31
forum: General Help
---

### Post by Patricrawley on 2008-08-31
I have a /home and a fat32 storage system that I use to get edit school things in windows with. I would like to keep a copy of my documents on both partitions and I was wondering is there anyway of automatically synchronizing them.

---

### Post by lswb on 2008-08-31
There are lots of options depending on your requirements. Is the fat32 dirve a separate external drive of some kind?

If it is a drive or partition installed in your system you may find it easier to simply mount it under linux and have the files accessible, rather than syncing copies between 2 partitions.

---

### Post by Patricrawley on 2008-08-31
It's on a seprate partition in the same drive but I don't want that to be my main Docements folder but I need a copy there to use in windows which I need for a few school neccesities. I want them to synchronize but I don't have any idea where to start.

---

### Post by fragos on 2008-08-31
Take a kook at Unison. I've successfully used in in similar situations.

---

### Post by monkeyking on 2008-08-31
What do you mean by sync'ing your files?

Do you just want a copy of files in 2 different locations?
I would just do rsync on login and logout,
Or that depends on the filesizes.

Or much more simple, why don't you just mount it,
so linux will work on the files directly.

---

### Post by fragos on 2008-08-31
Unison gives you copies of files in both places. It does a particularly good job of only copying files that have changed and supports changes made on both systems. If both systems changed the same file the user will be able to select the desired operation. Unison runs command line or on the GUI desktop. I manually initiate Unison since I sync over wireless between my laptop and desktop. Both run Ubuntu so I use NFS and manually initiate the mount before running Unison.

---

