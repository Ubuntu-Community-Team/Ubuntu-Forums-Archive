---
title: "Linux automounts in windows with full root priveleges"
date: 2008-08-07
forum: General Help
---

### Post by damick on 2008-08-07
This is more of a windows question than linux. I installed the ext3 filesystem on Windows, and now it mounts my ubuntu partition on startup with full read write access to everything, including passwd, shadow, all rc files, all home directories, et cetera. Is there any way to get windows to stop mounting on startup, or at least take away read/write access from some files or directories?

---

### Post by Taxman415a on 2008-08-07
What ext driver did you install? That would determine how to get it not to mount automatically on startup. If you use [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) there are setup options for that.

As far as the permissions, you're right, that is entirely a windows question, since permissions are not respected when you run a different OS. Consider the running OS doesn't even have the same users, so maintaining permissions would be tricky.

But I don't really run Windows anymore (man that's nice to say) so short of googling, I can't tell you anything about setting permissions on it.

---

