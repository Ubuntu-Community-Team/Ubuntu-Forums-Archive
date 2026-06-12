---
title: "How do I remove all file restrictions?"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by krazykuul on 2009-09-10
I know this has been asked before, but all the responses I saw were to go into sudo nautilus with the terminal (which I do), or change the permissions manually.

Since I am working with files mostly from programs I install, it is really annoying to have to change the permissions of each individual file.

So is there a way to completely remove all file and folder permissions?  I think I did it before, but that was a long time ago on another computer, and I totally forget how I did that.  I don't have to worry about security, and I am not dumb enough to go deleting files on my hard drive

Thanks for the help

---

### Post by StuartN on 2009-09-10
> **krazykuul said:**
> So is there a way to completely remove all file and folder permissions?

You can't remove the permissions, but you can make sure that they match the user. "sudo chown -R krazykuul:krazykuul *" will assign ownership to user krazykuul for all files in the current directory and recursively (-R) all files in subdirectories of the current directory.

You can then use "chmod -R +rw *" to make all files, directories and subdirectories readable and writable.

If you actually want to live without file ownership then you could transfer your files to an NTFS (or FAT) filesystem.

---

