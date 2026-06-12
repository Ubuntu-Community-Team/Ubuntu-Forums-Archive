---
title: "Directory shortcuts"
date: 2005-12-06
forum: General Help
---

### Post by WebDrake on 2005-12-06
Hello all,

Suppose I have a directory on a mounted partition---let's call it /media/hdaN/mydir .

Is there any way to set up a shortcut to point to that directory, so that referring to, e.g., /mydir , would be enough to get the contents of that directory?

Being inexperienced with Linux I tried simply adding some mount commands to the fstab file, but that didn't work (no surprise, really, since the directories are not themselves separate file systems).  Is there anything I can do that *will* work?

Many thanks,

       -- Joe

---

### Post by soulestream on 2005-12-06
you want a link

man ln <-- in terminal

ln -s, is probably what you want

soule

---

### Post by steve.horsley on 2005-12-06
```
ln -s /media/hdaN/mydir /mydir
```

---

### Post by WebDrake on 2005-12-06
Many thanks! :-)

---

### Post by Mr. Electric Wizard on 2005-12-06
In Gui form you can right click a directory, and select Make Link.
This will create the link in the same directory level that you are currently in.
You can Cut/Paste this link to wherever you want, like on the desktop.
After that you can rename the link to whatever you want and add an emblem or whatever too...
:D

---

