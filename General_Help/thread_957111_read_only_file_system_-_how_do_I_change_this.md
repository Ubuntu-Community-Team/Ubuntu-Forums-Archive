---
title: "read only file system - how do I change this?"
date: 2008-10-23
forum: General Help
---

### Post by hurtstotalktoyou on 2008-10-23
Hi, all.

I just bought a Sandisk Sansa e200 series mp3 player, and I used Ubuntu to add and delete some files.  When I did so, Ubuntu created a /.Trash-1000 directory.

Then I used the rockbox file manager (the software on the Sansa) to delete more files, possibly including some files in the /.Trash-1000 folder--although I don't remember for sure.  When I re-attached my Sansa to Ubuntu to add more files, Ubuntu mounted it as a read-only file system.  I can view files but I can't add or delete--at least, not from Ubuntu.

Windows treats it just fine.  I can add and remove files as normal.  But Ubuntu can't add or remove, because it thinks the player destination is read-only.

I think maybe the problem is the /.Trash-1000 folder.  But even though the Sansa works fine otherwise, it freezes when I try to delete the folder, and I have to reboot it.  I can't delete it from Windows, either.

After searching Google I came up with similar problems which were solved by running "fsck.vfat -a /media/<sansa location>".  I did so, but the file system is still interpreted by Ubuntu as read-only, and I still can't delete the /.Trash-1000 folder from rockbox on the Sansa itself, or from Windows.

How do I force Ubuntu to recognize my Sansa as read and write capable?

Any suggestions would be much appreciated!

---

