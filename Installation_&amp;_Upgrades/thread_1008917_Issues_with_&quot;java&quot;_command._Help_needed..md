---
title: "Issues with &quot;java&quot; command. Help needed."
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by MikeRaines on 2008-12-12
Hi guys,

I am working on a project, and while trying to fix something, I managed to get the openJDK as well as java6 installed. When I call the "java" command from the command line it fails due to some openJDK component. How do I retarget the "java" command to point to the java6 compiler?

Thanks!

---

### Post by Bear Knuckle on 2008-12-12
> **MikeRaines said:**
> Hi guys,

I am working on a project, and while trying to fix something, I managed to get the openJDK as well as java6 installed. When I call the "java" command from the command line it fails due to some openJDK component. How do I retarget the "java" command to point to the java6 compiler?

Thanks!

First of all, "java" is not the compiler (which is "javac"), it's the command to start a JVM and executed byte code.

You can run 
```
update-alternatives --config java
```
to reconfigure the "java" path.

---

### Post by jespdj on 2008-12-12
Note, update-alternatives must be run with sudo:
```
sudo update-alternatives --config java
```

---

### Post by Bear Knuckle on 2008-12-12
> **jespdj said:**
> Note, update-alternatives must be run with sudo:
```
sudo update-alternatives --config java
```

Damn, at least leave this small task to him, if not even the forums search was in his quest... ;-)

---

### Post by Poyntz on 2008-12-12
and if that doesn't work
1. backup the java files temporarily
2. uninstall java via synaptic or aptitude
3. ```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-source sun-java6-jdk
```

---

