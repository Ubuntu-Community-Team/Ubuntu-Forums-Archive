---
title: "How Can the Java cache folder be changed?"
date: 2008-09-11
forum: General Help
---

### Post by Dionysios on 2008-09-11
So, every time I run an application that uses Java, a folder is created on my Desktop, and inside it, I can see another folder called "cache", where I can see one more folder, called "http". In the latter folder, Java stores files that have to do with the applications I am running.
I have no folder called ".java" in my user home folder, so I suspect that java is looking for some place to store the cache files, and since it can`t see anything, it creates the cache on the Desktop.

Is there a way to change that, and create the proper place for Java to store the cache files?

Thank you in advance!

---

### Post by Denestria on 2008-09-11
Run the java control panel, it may be in your settings menu or Alt-F2 and enter 
```
ControlPanel
```
Look at the section that says temporary internet files, click the settings button, the location of the files can be edited there.

---

### Post by Dionysios on 2008-09-11
Thanks for the reply, Denestria.
So, I did that, but it says that the cache files are stored in the correct folder, namely ~/.java/deployment/cache.
I also tried to erase all the cache files, and the folder in the desktop is still there.I also try to clear all the cache from firefox, and it is still there on the Desktop.
If I erase this cache folder, it will be created again when I run a file that has to do with downloading stuff from the internet. It is not created for example when I run a .jar file.

Any more ideas?

Thanks!

---

### Post by Denestria on 2008-09-11
I'm afraid I have no idea.  Hopefully someone else will know.  The only other thing I can think of is Firefox trying to work offline?  Good luck!

---

### Post by Denestria on 2008-09-12
HA! Looks like I got it.  Have a look in your home directory for a file called .netxrc
Mine looks like this

less .netxrc

```

#netx file
#Thu Sep 11 22:18:03 CDT 2008
basedir=/tmp

```

When I changed the basedir to my desktop the cache/http directories appeared on my Desktop.  I think this is from the icedtea-gcjwebplugin.

Now I can sleep at night.  :D

---

### Post by Dionysios on 2008-09-12
Denestria, you are a genius!!!

Thank you SO much!  :)

---

