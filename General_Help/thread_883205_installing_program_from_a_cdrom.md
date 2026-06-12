---
title: "installing program from a cdrom"
date: 2008-08-07
forum: General Help
---

### Post by zellett on 2008-08-07
Hello,

I've got 64-bit Ubuntu 8.04 and I've been trying to install IDL 6.4 (3d visualization data processing).  The program is on a CD and I can get the installer to run, but it says I don't have write access to the default installation directory (/usr/local/itt).  I've tried to change it to someplace that can be written to, but several other components of the program seem to also try to install to the filesystem (which if I understand correctly, can't be written to? (I'm not sure why that is, but it seems excessive)).  At the end, it says the installation is complete, but with errors.  And if I check the installation directory, no files have been copied.

I've only been using linux for a couple weeks, and this is the first program I've tried to install (like I would in Windows, from a CD).  I can't believe that nothing can be written to the filesystem.  You know like when you install a program in Windows, it is installed in the Programs Files folder.  How am I supposed to install something if the default folder is write protected.  Its the default folder for a reason.  Is there something more I need to be doing?

Sorry about the rant, but not used to how Linux deals with these things.

---

### Post by spiderbatdad on 2008-08-07
perhaps chown the folder:```
sudo chown zellett:zellett /usr/local/itt
```

then make sure it is writable:```
sudo chmod u+w /usr/local/itt
```

---

### Post by spiderbatdad on 2008-08-07
I totally understand your frustration. Most linux programs install smoothly without hassle. Who is the manufacturer of this cd? Are there any instruction or support available?
There are other tricks that can be used like chowning /usr/local/src and using that as a prefix for installation...this all can seem technical and beyond what should be required for a modern computing system, but consider if your software was not specifically designed for the operating system...some steps have to be taken to make it work.

---

