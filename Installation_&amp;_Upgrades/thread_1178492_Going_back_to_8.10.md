---
title: "Going back to 8.10"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by frogbrains on 2009-06-04
As the Intel graphics drivers in 9.04 are completely broken (Especially in Blender.  Suprisingly, desktop effects work fine.) I decided to go back to 8.10, which I have used before.  Is there a way of down-grading Ubuntu without losing all my programs and stuff, because I have been using 9.04 for... well... since a couple of days after it came out, and I already have quite a lot of stuff.  How do I go about backing up all my documents, music, programs etc.?  Also, if I backed up my programs, would they still appear in the Applications menu in 8.10?

---

### Post by whoop on 2009-06-04
As far as I know there is no official way to downgrade...

---

### Post by freakyruft on 2009-06-04
I'd backup to be sure (if possible, dd image), but...

I think you can keep your home drive (if it's on another partition, if not you'll have to backup /home), and just copy the paths /etc, /var and /usr/local and copy back after the installation, should work.
To backup your programms 
```

sudo dpkg --get-selections | grep "\binstall" | awk '{print $1}' > backupfile-apt.log

```
, to restore it you can use
```

sudo xargs -n1 apt-get install -y < backupfile-apt.log

```
Then the programs are of course in the menu (all reinstalled, settings kept from your /home-folder).

haven't tried, but should work.

---

### Post by frogbrains on 2009-06-04
Thanks!  I'll try this!

---

