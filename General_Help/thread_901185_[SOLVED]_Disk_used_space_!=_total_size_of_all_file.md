---
title: "[SOLVED] Disk used space != total size of all files"
date: 2008-08-26
forum: General Help
---

### Post by dugald on 2008-08-26
In system monitor my disk is 91% full:

```
Free: 9.6 GB
Available: 5.5 GB
Total: 68.9 GB
Used: 59.6 GB
```

So I tried to find out which files are taking up all of the space.  My Home folder is only 9GB.  If I start nautilus as root, select all folders in / and go to properties, it says the total is 20.1 GB (not the 59.6GB as stated in the system monitor).

Where has all my space gone?  Where should I be looking?

---

### Post by jigsaws on 2008-08-26
Purge the trash. If problem still exists try:
sudo du -ks /*

It tells you which directory is big. Then follow du in this directory.

---

### Post by jedi-penguin on 2008-08-26
hmmmm, does nautilus count hidden files?

---

### Post by dugald on 2008-08-26
Thanks for suggesting the du command - it showed me that the culprit was in the /home directory, but when I went there and ran the command again, I couldn't find the cause.

I did some research and ran ```
du -ms /home/dugald/*.[a-zA-Z0-9]*
``` and I doscovered that the cause is indeed a hidden directory containing a VirtualBox machine.

---

