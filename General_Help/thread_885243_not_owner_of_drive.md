---
title: "not owner of drive"
date: 2008-08-09
forum: General Help
---

### Post by lilmill on 2008-08-09
I had taken one of my old drives and put it in an external case, but I cannot write to drive. It says I am not the owner. I am able to reformat with the partition editor I have tried ext2 & 3 and reiserfs all say the same. Why would it let me reformat but they say i cant use it. Any help would be appreciated im still trying to get ahold of linux.

---

### Post by Herman on 2008-08-09
:) Hello lilmill,
It sounds like a file permissions and ownership issue.

To check, just open up a terminal, and copy and paste this command into it,
```
ls -l /media
```Examine the output from that command.
Likely your USB drive will just be called 'disk' there. I am guessing that the mount point is owned by root.
You can change the ownership of the mount point with a chown command.
```
sudo chown lilmill.lilmill /media/disk
```Try that and see if it solves your problem. :)

---

### Post by lilmill on 2008-08-09
that fixed it thanks a lot. More to add to my notes.

---

