---
title: "no ndiwrapper.ko directory?"
date: 2008-11-30
forum: General Help
---

### Post by nevercroft on 2008-11-30
I just finished installing ndiswrapper and my wifi adapter in Intrepid but when I run 
```
sudo modprobe ndiswrapper
```

I get this error:

```
 groff@groff-desktop:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
groff@groff-desktop:~$ 

```


I've installed the, utils, ndiswrapper-1.52, and ndisgtk from here: 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
under the section for installing with another computer with internet access  

ndisgtk detects my hardware when I plug it in.


I'm so close and the fact that I can't use wireless is the only reason I havn't made a complete switch to ubuntu (i'm dual booting with xp).

---

### Post by cariboo on 2008-11-30
Did  you check to see if ndiswraper was located in the directory mentioned in the error?

Jim

---

### Post by nevercroft on 2008-11-30
Yes, ndiwrapper.ko is not there.

---

