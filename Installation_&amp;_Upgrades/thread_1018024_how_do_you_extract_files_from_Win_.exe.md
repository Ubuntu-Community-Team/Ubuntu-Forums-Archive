---
title: "how do you extract files from Win *.exe"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Sierra_Dave on 2008-12-21
Hi,

I need to extract some driver files from a Windows setup.exe file.  Is that possible from inside Ubuntu and ,if so, how?
Dave:confused:

---

### Post by zvacet on 2008-12-21
You can not install exe files in Ubuntu (or in any other linux distro) because they don´t use it.It is better to start new thread and be specific what problem  you have.What do you need to install,what problems do you have trying to do that and so on.

---

### Post by albinootje on 2008-12-21
> **Sierra_Dave said:**
> Hi,

I need to extract some driver files from a Windows setup.exe file.  Is that possible from inside Ubuntu and ,if so, how?
Dave:confused:

Depending on the format of those exe files you can try to use "cabextract" or "unzip".
But much easier is to install Wine, and use that.

---

### Post by night_fox on 2008-12-21
Sometimes a .exe file can be a self extracting archive, which can be opened with ubuntu's archive manager, but this probably isn't one of them, so I would use wine or windows, or just download the uncompressed driver files.
I take it you are getting them for use in ndiswrapper?

---

