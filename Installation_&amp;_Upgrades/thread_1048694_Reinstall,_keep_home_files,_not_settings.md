---
title: "Reinstall, keep home files, not settings?"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by c-roc on 2009-01-23
I've got a big home partition, so would like to avoid moving stuff around.. can I do a fresh install on the / partition, then tell it to use my home partition as home, but after I've deleted all the .folders ?  will that be a FRESH install?

I think I've messed some stuff up so I want to start fresh rather than upgrade, but I have too many data files in my home folder to back up or move.

easiest solution?

thanx!

I have three partitions, /, swap, and home on one disk.

---

### Post by taurus on 2009-01-23
If you don't want to keep all your old settings, you can delete all those files and directories with the . in front.  You can keep all other directories since you have your personal files in there.  Then, when you log in the first time after you have reinstalled it, it will create all those new .files & .directories for you, giving you the default settings.

Just remember to mount that partition to /home but do not format it during the installing process.

---

### Post by c-roc on 2009-01-23
would it be safer then to NOT map home to my home partition, then move it after?  or maybe it doesn't work that way...

So it's fairly easy to do what you're saying without accidentally formatting the home partition?

thanx again.

---

### Post by taurus on 2009-01-23
It's best to mount that partition to /home during the installing process.  Then, you don't have to worry about mounting and moving stuff over later.  Should be real easy as long as you remember not to put a check mark in a box next to the mount point, formatting.  Just double check everything before you move to the next step.

---

### Post by c-roc on 2009-01-23
sorry for nitpicking here....


so I can delete all .files in home, then logout, then boot from disk.. or I guess I can just delete all .files in home, then just stick in the disk and tell it to format / and use my home partition as home.
So by doing that I'll have just as completely fresh an install as I would if I had formatted everything?  it's that simple, just the .folders/files?

thanx again for the quick responses..

---

