---
title: "Dual Booting Troubles"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by mykeljee on 2009-07-16
I just attempted to install Ubuntu 9.04 Netbook Remix on my acer aspire one, I had already made an extra partition using Windows XP. So when I go to the partition selection screen I chose the one I made and I get the error: "No root filesystem."

---

### Post by merlinus on 2009-07-16
Rightclick on the partition, and you should get a dropdown menu with mountpoints.  Choose / (or root).

---

### Post by mykeljee on 2009-07-16
What type of partition should it be? ntfs, fat32, ex2, ex3, etc.

Because by default it's ntfs and the mountpoints for that are /dos and /windows, I'm assuming not for linux..

---

### Post by merlinus on 2009-07-16
I recommend ext3.  But be sure that you are not selecting your windows partition, or it will be gone!

---

### Post by mykeljee on 2009-07-16
Works like a charm! Thanks so much. I've been using ubuntu for like a week now and this is why I love it: community!

---

### Post by merlinus on 2009-07-16
Excellent!  Have fun, and post back if you run into difficulties.

---

### Post by mykeljee on 2009-07-17
Hah actually I have ran into a problem. Frequently the top windows bar, or any new opened window for that matter just disappears. It's still there but I can't see it haha. Sounds strange doesn't it? I'm assuming there was something wrong with the iso when I installed it.. or is this a common problem

---

