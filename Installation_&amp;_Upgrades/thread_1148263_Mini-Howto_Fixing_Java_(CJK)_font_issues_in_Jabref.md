---
title: "Mini-Howto: Fixing Java (CJK) font issues in Jabref after Jaunty install"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by guba on 2009-05-04
Problem: many Characters are not rendered correctly in JabRef after a clean Jaunty install. 

Reason: Java has no access to the correct fonts.

(If you have a JabRef-Java issue but not a CJK problem, then only the first part of this Howto is of relevance to you.)

Solution:

First of all: install sun-java:

```

$ sudo apt-get -y install sun-java6-jre 
$ sudo apt-get -y install sun-java6-jdk 
$ sudo apt-get -y install sun-java6-fonts 
$ sudo apt-get -y install sun-java6-plugin 

```

Then:

```

$ JAVA_HOME=/usr/lib/jvm/java-6-sun
$ export JAVA_HOME 

```

Figure out where your system's Chinese fonts are, e.g. simsun.ttc from M$, at /usr/local/share/fonts:

```

$ cd $JAVA_HOME/jre/lib/fonts
$ ln -s /usr/local/share/fonts fallback 

```


Sources: 
[http://blog.lizhao.net/2007/03/java-chinese-fonts-on-ubuntu.html](http://blog.lizhao.net/2007/03/java-chinese-fonts-on-ubuntu.html)
[http://nxadm.wordpress.com/2008/09/16/a-bibliography-manager-for-nx-jabref/](http://nxadm.wordpress.com/2008/09/16/a-bibliography-manager-for-nx-jabref/)

NOTE: if you want to have the GTK Look&Feel instead of the standard java Look&Feel, go to Options->Preferences->Advanced and specify "com.sun.java.swing.plaf.gtk.GTKLookAndFeel" as class name.

That's all, folks!

Guba

---

