---
title: "I have installed JRE 6, but when typing java..."
date: 2008-11-09
forum: General Help
---

### Post by B12 on 2008-11-09
I just finished installing JRE6. After I typed:
```
sudo update-alternatives --config java
```
I had this as one of my options:
```
/usr/lib/jvm/java-6-sun/jre/bin/java
```
However, when I type in "java", I get:
```
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: apt-get install <selected package>
-bash: java: command not found

```
When I try to run a java-based .sh file, I get:
```
10: java: not found
```

How do I fix this? Thanks.

---

### Post by taurus on 2008-11-09
Post the complete output when you run this command again.

```
sudo update-alternatives --config java
```

---

### Post by lsutiger on 2008-11-09
[Try this link]("http://http://www.ubuntu1501.com/2007/05/installing-java-runtime-environment-6.html") to install java

---

### Post by bielawski on 2008-11-09
> **lsutiger said:**
> [Try this link]("http://http://www.ubuntu1501.com/2007/05/installing-java-runtime-environment-6.html") to install java
I think you meant to say "[Try this link]("http://www.ubuntu1501.com/2007/05/installing-java-runtime-environment-6.html")".

---

### Post by bielawski on 2008-11-09
What version of Ubuntu do you have? What is in your /etc/apt/sources.list ?

---

