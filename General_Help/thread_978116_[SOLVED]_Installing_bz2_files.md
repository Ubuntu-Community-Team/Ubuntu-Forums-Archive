---
title: "[SOLVED] Installing bz2 files"
date: 2008-11-10
forum: General Help
---

### Post by Rubicon421 on 2008-11-10
Anybody want to help a total newb install a bz2 file? PM me, reply or message me on MSN. Thanks!

---

### Post by Pro-reason on 2008-11-10
No, please don't ask for individual help on the forums.  They are here so that people can fully explain their problem, and others can come and help out.  It is done openly so that other people can benefit from it.

Files ending in .bz2 are not for installing, in particular.  They are just compressed files, just like .zip.

What program are you trying to install?  In all likelihood, it is available in Synaptic.

---

### Post by spibou on 2008-11-10
You uncompress the file by doing (on the command line) **bzip2 -d file** I'm not sure what you mean by "install". What's in the file?

---

### Post by thibeaz on 2008-11-10
more or less what is the file found at so we can help you further

---

### Post by Rubicon421 on 2008-11-10
It's the listen music player.

---

### Post by Rubicon421 on 2008-11-10
[http://www.listen-project.org/](http://www.listen-project.org/)

---

### Post by spibou on 2008-11-10
**apt-get install listen** should install it.

---

### Post by Rubicon421 on 2008-11-10
I just found it in the add remove programs, guess I didn't need to download the bz2 at all.

---

### Post by Pro-reason on 2008-11-10
> **Kill Vista said:**
> [http://www.listen-project.org/](http://www.listen-project.org/)

That archive contains source code.  If you don't know what bz2 is, then you're not an expert, and thus shouldn't be trying to compile source code.  

Moreover, the source code checks for PyGTK in a faulty way.  It is unable to detect it installed as &#8220;python-gtk&#8221; on Ubuntu.  I've not sure how to get around this without a lot of fiddling with the Python code.

Just use a program from Synaptic.

---

### Post by Rubicon421 on 2008-11-11
> **Pro-reason said:**
> That archive contains source code.  If you don't know what bz2 is, then you're not an expert, and thus shouldn't be trying to compile source code.  

Moreover, the source code checks for PyGTK in a faulty way.  It is unable to detect it installed as &#8220;python-gtk&#8221; on Ubuntu.  I've not sure how to get around this without a lot of fiddling with the Python code.

Just use a program from Synaptic.
Thanks, and no offense taken to the expert remark. I totally agree. I am somewhat of an expert in Windows (which I will never go back to, except for some occasional gaming) but that knowledge is useless here. I've suddenly became the newb that I use to have to help all the time and I really appreciate anyone willing to do the same. 
BTW- love the signature!

---

