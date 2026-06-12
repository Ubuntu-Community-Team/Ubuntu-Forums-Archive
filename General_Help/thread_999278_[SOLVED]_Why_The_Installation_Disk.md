---
title: "[SOLVED] Why The Installation Disk?"
date: 2008-12-01
forum: General Help
---

### Post by brook adams on 2008-12-01
I bought my laptop with Ubuntu 7.10 pre-installed. Recently I upgraded to 8.04. I had some difficulty which resulted in my installing 8.04 from a free disk I got from Linux-Pro Magazine. This worked out fine but as I go about my business installing the occasional bit of software the OS will sometimes require me to insert the installation disk.

I remember windows used to do that too and I would like to know what is the purpose of that? I keep the disk handy but I would prfer not to need that.
Is there a way to change it?

Thanks in advance...

---

### Post by oldos2er on 2008-12-01
Go to System, Administration, Software Sources, and uncheck the box next to CD-ROM/DVD.

---

### Post by adult swim on 2008-12-01
this happens because the installation disk is marked to be checked for updates.  to take care of this, press alt+f2 and run ```
gksudo gedit /etc/apt/sources.list
``` then go to the line that starts ```
deb cdrom
``` which should be the very first line and put a # in the very front of the line so it looks like this ```
# deb cdrom
```  then save and close the file and you should be all set.

---

### Post by brook adams on 2008-12-01
I thank you all kindly...

That certainly does the trick.

---

