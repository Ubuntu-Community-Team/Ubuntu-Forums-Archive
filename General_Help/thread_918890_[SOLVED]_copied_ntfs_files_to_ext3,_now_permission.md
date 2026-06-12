---
title: "[SOLVED] copied ntfs files to ext3, now permissions screwed and can't read files prop"
date: 2008-09-13
forum: General Help
---

### Post by sadohert on 2008-09-13
I can't seem to even find *SOMEWHAT* related posts to try to figure out what my problem is, so I decided to just post.

I'm fixing up a friends XP box.  As an intermediate step I stuck his harddisk in my linux box and copied all his documents over to my machine.  My next step is to blow away everything on his hd and re-install fresh.

The problem is I can see the root of the copied filesystem, and if I "sudo ls" at certain points in the directory structure I can still see all the files, but I can't change the owner or permissions on them, and can't read the directory tree in the normal way.  In gnome terminal the files all appear in red font, with question marks for the owner/permissions stuff.

I tried copying a single word doc using "sudo cp <weird filesystem file> <my linux desktiop> and the file is fine, and I can read it no problem.

Anyway know what might be goign on here, and how I might get around this.

---

### Post by Neo_The_User on 2008-09-13
Type this into the terminal

gksudo nautilus

Then you should be able to access and re-write anything you like.

---

### Post by sadohert on 2008-09-13
Dude.... thank you so much for the quick and helpful response.  That's exactly what I needed to get at those files.

I'm still curious about what has happened here though.  I'm sure I probably "sudo"'ed to copy all these files off the drive onto my local filesystem, so I understand they would all have root ownership.  BUt why on earth can I not change those to be my normal user?  What the heck was going on there, and whats with the red questions marks?

Anyway, thanks a lot.

Stu

---

### Post by Neo_The_User on 2008-09-13
No problem and you are very welcome! And the reason why, I have no idea. I just do what works regardless of the reason.

---

### Post by sadohert on 2008-09-14
Alright, for anyone who stumbles across this post in the future, it looks like the problem with the questions marks was that none of the directories had the executable bit set.  Once I set the x bit on all the directories, and changed ownership to my normal user, everything started working okay again.  

Stu

---

