---
title: "How to find recent installs"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by CodeNosher on 2009-08-03
Hello,

I have a problem with installing several things at once using aptitude then forgetting what I just installed.  I know, I know, but I'm an impulse downloader.  

Is there a good way to find out what I've installed in a date sequence?

Thanks

---

### Post by cjv8888 on 2009-08-03
> **CodeNosher said:**
> Hello,

I have a problem with installing several things at once using aptitude then forgetting what I just installed.  I know, I know, but I'm an impulse downloader.  

Is there a good way to find out what I've installed in a date sequence?

Thanks

Pressing up arrow at the terminal will give you all the previous terminal commands or you can have a look at .bash_history in your home directory.

---

### Post by sarfarazkazi on 2009-08-03
Have a look at the log file /var/log/dpkg

---

### Post by CodeNosher on 2009-08-14
Those are the logs I was looking for.  A bit difficult because it shows all the required packages, too, but at least it is there.

Thanks.

---

