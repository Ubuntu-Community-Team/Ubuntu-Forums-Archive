---
title: "Help"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by ffgc on 2009-09-30
Then i install sun-java6-bin i get this error
Hawe not install noting els 


root@aktiv-web-01:/var/lib/dpkg# sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-demo: Depends: sun-java5-jre (= 1.5.0-19-0ubuntu0.9.04) but it is not going to be installed
                  Depends: sun-java5-jdk (= 1.5.0-19-0ubuntu0.9.04) but it is not going to be installed
  sun-java6-bin: Depends: sun-java6-jre (= 6-16-0ubuntu1.9.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).:confused:

---

### Post by rob-ward on 2009-09-30
Try this command to install the jdk instead of the bin, that should give you what you need:

```
sudo apt-get install sun-java6-jdk
```

Let us know if that works

---

