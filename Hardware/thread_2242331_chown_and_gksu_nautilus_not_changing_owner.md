---
title: "chown and gksu nautilus not changing owner"
date: 2014-09-01
forum: Hardware
---

### Post by Hamburgian on 2014-09-01
a bad .deb changed owner of my internal ext4 partitions. They are now owned by 'Me', not my user name. 
I've tried gksu nautilus and chown -R commands, but the owner remains 'Me'.
I'd like to move my /home directory to one of these ext4 partitions, but if I do so, the owner of the root partitions gets changed too. 
I've already reinstalled one 14.04 system, and reinstalled another from a backup, but the chown and gksu nautilus command have no effect.

---

### Post by steeldriver on 2014-09-01
How are you determining that the owner is 'Me' (in nautilus, or using the 'ls -l' command in a terminal)? In nautilus, 'Me' is just used as a synonym for the owner of the current desktop session.

---

### Post by Hamburgian on 2014-09-01
OK..thanks for that. Is this a new synonym? I hadn't noticed it in 12.04, I've just updated and had a panic attack. How do I mark this as 'solved'?

---

### Post by steeldriver on 2014-09-01
there was lots of discussion a while back e.g. this --> [https://bugzilla.gnome.org/show_bug.cgi?id=680282](https://bugzilla.gnome.org/show_bug.cgi?id=680282)

---

