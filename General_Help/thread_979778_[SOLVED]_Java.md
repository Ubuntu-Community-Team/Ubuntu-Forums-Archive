---
title: "[SOLVED] Java"
date: 2008-11-12
forum: General Help
---

### Post by plasmarox on 2008-11-12
Hello all;

Ive downloaded the java *.bin, renamed to to *.run and extracted fine to my desktop, but i dont know what to do next.

Any ideas? :D

---

### Post by nikgare on 2008-11-12
What are you tying to do?
If you just want to install java, you can do it via Synaptic

---

### Post by oldos2er on 2008-11-12
> **plasmarox said:**
> Hello all;

Ive downloaded the java *.bin, renamed to to *.run and extracted fine to my desktop, but i dont know what to do next.

Any ideas? :D

 No need to rename or extract it. If the file's on your desktop, open a terminal and run these commands one at a time:

 cd Desktop

 chmod a+x java*bin

 sudo ./java*bin

 Replace java*bin with whatever the filename is.

 Or, as was suggested, install Java using Synaptic Package Manager.

---

### Post by jespdj on 2008-11-12
The preferred way to install software on Ubuntu is via the package management system. If you are trying to install the latest version of Sun Java 6, look for packages named **sun-java6-...** in Synaptic. You can also install it in a terminal window:
```
sudo apt-get install sun-java6-plugin
```
This will install the JRE and browser plug-in (for 32-bit Ubuntu only). If you want to install the JDK (because you want to compile your own Java programs):
```
sudo apt-get install sun-java6-jdk
```

---

### Post by plasmarox on 2008-11-13
Thanks alot. I used apt-get for this :D
Ive marked this post as solved.

---

