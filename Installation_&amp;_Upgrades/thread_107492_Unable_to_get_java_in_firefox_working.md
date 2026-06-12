---
title: "Unable to get java in firefox working"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by alamba on 2005-12-23
Hi,

I installed the java package (jreXXXX.bin file) from the sun site. And followed the steps in the following thread:

[http://www.ubuntuforums.org/showthread.php?t=76754&highlight=Java+plugin+firefox](http://www.ubuntuforums.org/showthread.php?t=76754&highlight=Java+plugin+firefox)

However, the output I get from running java -version is:
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

What do I need to do to get java running? What am i missing here?

tia

Akshay

---

### Post by kaamos on 2005-12-23
Try this:
```
sudo update-alternatives --config 
```

---

### Post by r0ll3r on 2005-12-29
```
sudo update-alternatives --config java
```

---

