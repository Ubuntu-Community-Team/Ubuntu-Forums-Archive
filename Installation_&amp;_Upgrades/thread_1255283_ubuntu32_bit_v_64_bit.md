---
title: "ubuntu32 bit v 64 bit"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by baconbuttyman on 2009-09-01
will ubuntu 64 bit run on my machine (see signature)
i have heard it will and there are advantages to using 64 bit, is this true

---

### Post by pythonscript on 2009-09-01
There are some advantages to using 64-bit, but there are also disadvantages. 64-bit systems support more memory (in this case, all of your 4 gb of memory) but also takes twice as much to run. Some linux hardware drivers are not supported under 64-bit, as is adobe flash player (fully). See what other people have to say before you install 64-bit. If your main goal is getting access to all 4 gb of memory:

```
sudo apt-get install linux-server linux-headers-server
``` will give you the server kernel that supports 4 gb of memory, but still with the 32-bit hardware support.

---

### Post by presence1960 on 2009-09-01
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

if you have a dual core CPU it is 64 bit capable. 64 bit is stable now including Flash.

---

