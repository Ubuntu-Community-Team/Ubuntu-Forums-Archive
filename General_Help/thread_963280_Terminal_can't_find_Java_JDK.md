---
title: "Terminal can't find Java JDK"
date: 2008-10-30
forum: General Help
---

### Post by karl_eller on 2008-10-30
Alrighty, so I installed NetBeans 6.1 and Java JDK 1.6 Update 7 using the downloaded file from the Java website, and everything is installed correctly. However for reasons I don't quite understand, NetBeans installed the Java JDK to /usr/local/jdk1.6.0_u7, and the terminal doesn't think there is a JDK installed ("javac" returns the usual "this program isn't installed, use apt-get to download one of the following packages" message). So short of installing another JDK/reinstalling JDK 6U7, is there any way to get the JDK working in terminal? It's working fine in NetBeans, it'll compile and run programs properly.

Eller

---

### Post by fyo on 2008-10-30
Sounds like you just need to add it to your path. The easiest way is probably just linking (ln -s) to javac from /usr/local/bin:

```
$ ln -s /usr/local/jdk1.6.0_u7/javac /usr/local/bin/javac
```

or whatever the correct locatation of javac is.

---

### Post by karl_eller on 2008-10-30
Cheers mate, that did the trick (javac was in /usr/local/jdk1.6.0_u7/bin/).

Out of curiosity, if I was to update to a different JDK in the future (eg JDK 6 u10 or whatever) using either APT or the Java installer, would I need to delete and/or re-create that link, or would it most likely get over-writen when the new JDK was installed?

Eller

---

### Post by fyo on 2008-10-30
The link will go to the exact location specified ( /usr/local/jdk1.6.0_u7/javac ), so if you install a new jdk in a different location (say /usr/local/jdk1.6.0_u8/javac ), the link would need to be updated accordingly.

---

