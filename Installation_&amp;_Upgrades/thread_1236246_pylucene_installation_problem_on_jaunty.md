---
title: "pylucene installation problem on jaunty"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by harry2006 on 2009-08-10
i've been trying to install pylucene on my box for last couple of days, but not yet able to do so. i did follow the instructions give in this thread, 
  [http://ubuntuforums.org/showthread.php?t=593327](http://ubuntuforums.org/showthread.php?t=593327)
i used the gcj one, and after doing all the steps i got the following error when trying to import the pylucene module,
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import PyLucene
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named PyLucene
>>> 

i must mention that i'm using python2.6 that comes by default with jaunty, and did all the substitution of 2.5 by 2.6 as the above thread refers to python2.5 version.
then when i tried to use apt-get i got the following error;
sudo apt-get update
[sudo] password for harry: 
apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.9-6.so.4.7)
then i tried removing the those two .so files copied to the /usr/local/lib directory as mentioned in the thread and after running sudo ldconfig, apt-get issue was got resolved, but the pylucene is still stuck at the same place. 
can someone help me fixing the issue. 
literally i'm pissed offff...sorry for the language..but thats the fact...

thank you

---

