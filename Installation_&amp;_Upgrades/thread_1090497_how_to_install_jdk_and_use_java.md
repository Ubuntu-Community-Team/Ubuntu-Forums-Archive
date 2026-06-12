---
title: "how to install jdk and use java"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by smartboinc on 2009-03-08
I just download the jdk from java.sun.com, the file jdk-6u12-linux-i586.bin and i have installed using command sudo jdk-6u12-linux-i386.bin, but now when i type the command java, it tell me the programme 'java' can not be found, and "Try sudo apt-get install....'. is there something wrong, what should i do

---

### Post by taurus on 2009-03-08
Do you remember where you unpacked jdk-6u12-linux-i386.bin?  And if you want java, should install the one from the repos, much easier.

```
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

---

