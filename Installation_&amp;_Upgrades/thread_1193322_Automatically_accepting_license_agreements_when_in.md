---
title: "Automatically accepting license agreements when installing from repo"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-06-21
I've set up a small shell script that downloads and installs from the main repositories all of the software packages that I use, so when I install ubuntu, I run the script and all the packages are there. The only question I have is about the Sun JDK. I'm using 

```
sudo aptitude install sun-java6-jdk -y
```

to download and begin installing the package, but I'm wondering if there's a way to automatically accept the license agreement while still using the package from the repository. I'd like to have this entire installation automated, and any tips would be greatly appreciated. Thanks in advance!

---

### Post by pythonscript on 2009-07-11
Should I just find the source on Sun's website and compile that into a .deb, or would that not work?

---

