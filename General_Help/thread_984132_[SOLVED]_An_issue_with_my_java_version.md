---
title: "[SOLVED] An issue with my java version"
date: 2008-11-16
forum: General Help
---

### Post by Nednull on 2008-11-16
I have a minor problem with java that I can't find out of on my own..

```
java -version
```
produces this output:
```
java version "1.5.0"
gij (GNU libgcj) version 4.3.2
```

Should be 1.6.x, but I don't really know what I did to screw it up. I have the following packages:
```
sun-java6-bin
sun-java6-jdk
sun-java6-jre
```

Probably an easy fix, but I don't know where to begin. Thanks in advance :)

---

### Post by taurus on 2008-11-16
Have you installed Sun's version?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

When you are presented a java licensing window, press the Tab key to highlight the <OK> and Return to except it.  It will not install unless you except the license first.

---

### Post by binbash on 2008-11-16
after installation you need to : 

sudo update-java-alternatives -l 

and select (sudo update-java-alternatives-s ) sun java.

---

### Post by jamesstansell on 2008-11-16
> **Nednull said:**
> 

Probably an easy fix, but I don't know where to begin. Thanks in advance :)

Most ubuntu/debian packages install their information about the package in the /usr/share/doc/ directory, so beside asking in the forums that's a great place to begin.

In your case, in the /usr/share/doc/sun-java6-jre/ directory the README.alternatives file may be of the most interest.

In general, README.Debian is a great place to start.

-james.

---

