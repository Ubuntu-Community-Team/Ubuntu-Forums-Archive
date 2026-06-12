---
title: "Partition Size Help"
date: 2008-09-11
forum: General Help
---

### Post by keenish27 on 2008-09-11
I am going to be setting up a new ubuntu box and would like to make my home drive on a second partition.  The problem I'm running into is that I'm not sure what sizes to make the partitions.  Will the main system partition be using more space for file installs, or will my home drive partition be using more?  Any insight will be much appreciated.

---

### Post by gvartser on 2008-09-11
Well it all depend on what you will store in your /home partition and how many users etc..

If you store movies, music etc then the /home will use more then if you just use it for storing docs and environmental configurations.


/g

---

### Post by bingoUV on 2008-09-11
I can't tell you exact amounts you should use but hope this helps.

Out of my 160GB hard disk, I use

1. 6GB for swap. It is too much for most people. Generally I recommend 2GB.
2. 10GB for /. It will be rare to need more than this
3. 10GB for /home. I don't store all my data in home, so it makes sense for me. If you store all data in your home directory which is sensible, allocate all the rest of your storage to /home.
4. Miscellaneous.

---

### Post by keenish27 on 2008-09-11
Thanks for all of the help.  I have a server set up that stores my media.  So home would be for documents and such.  I've been using Ubuntu for a while, but I'm still learning the ins and outs.  I just wanna make sure, but where do the installed programs generally go?  /usr/bin?

---

### Post by bingoUV on 2008-09-11
> **keenish27 said:**
> but where do the installed programs generally go?  /usr/bin?

It is not that simple, that is why a package manager like deb (and associated programs like apt-get, dpkg, aptitude, synaptic etc) are so important.

Generally they go into /usr/bin, /usr/lib, /usr/share/, /etc and some others. The running program would create log files, crash files etc. in /var. Most programs, however, would not add anything to /home when installing.

When a programs runs for the first time, it will generally create files in the home directory of the user which runs them. These files will be for storing configuration, cache, lock files etc.

---

### Post by keenish27 on 2008-09-11
Ok, that clears things up a lot.  Thanks for all of your help.  I guess my last question would be about Cedega.  I know this isn't a Cedega forum...but where would those files go.  I know wine creates a windows directory structure in a hidden folder somewhere, but don't remember where.  Would this be in home?  or elsewhere?

---

