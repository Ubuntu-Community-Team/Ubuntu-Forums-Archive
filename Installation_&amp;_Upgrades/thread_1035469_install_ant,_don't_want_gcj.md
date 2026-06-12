---
title: "install ant, don't want gcj"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by bartvh on 2009-01-09
I'm running mythbuntu 8.10. I want to install apache ant, after having installed sun-java6-jdk.

```
$ sudo apt-get install ant
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  ant-gcj ant-optional ant-optional-gcj gcj-4.3-base libgcj-bc libgcj-common libgcj9-0 libgcj9-jar libjaxp1.3-java libjaxp1.3-java-gcj
  libxerces2-java libxerces2-java-gcj
Suggested packages:
  ant-doc libbsf-java liboro-java libxalan2-java junit liblog4j1.2-java libregexp-java jython antlr libbcel-java libcommons-logging-java
  libjdepend-java libgnumail-java libxml-commons-resolver1.1-java libcommons-net-java libjsch-java javacc libgcj9-dbg libgcj9-0-awt
  libxerces2-java-doc
The following NEW packages will be installed:
  ant ant-gcj ant-optional ant-optional-gcj gcj-4.3-base libgcj-bc libgcj-common libgcj9-0 libgcj9-jar libjaxp1.3-java libjaxp1.3-java-gcj
  libxerces2-java libxerces2-java-gcj
0 upgraded, 13 newly installed, 0 to remove and 113 not upgraded.
Need to get 27.5MB of archives.
After this operation, 63.1MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

How can I make it not get GCJ? I don't want that stuff.
Or am I missing the point here, and won't it install GCJ at all?

How can I get ant on my computer? Thanks :)

---

### Post by leorochael on 2009-12-08
There is a [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/96423") dealing with this.

You can work around it typing on the console (for karmic):

```

sudo apt-get install ant ant-gcj- ant-optional-gcj- gcj-4.4-base- libgcj-common-

```Hope it helps

---

