---
title: "desperate java installation"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by eschilo on 2009-04-30
[SIZE=2]hallo you all!
I have problems in installing the latest java version 6_13 on ubuntu 8.04
I read a lot of post but i could not find the solution and now i am quite desperate...
on my laptot an older java version 6_07 is installed, and even if the istallation of the new one was succesful, firefox seems to continue to use the old one. What can I do?
if I type java -version it appears the new one:
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Client VM (build 11.3-b02, mixed mode, sharing)
 :confused::confused::confused::confused:
please help!!!

[/SIZE]

---

### Post by taurus on 2009-04-30
Did you remember to install the plugin?  If you install Sun java by hand, you need to link it to /usr/lib/mozilla/plugins.

---

### Post by eschilo on 2009-05-01
thank for your reply, but I have already installed plugins.
In my laptop I have three directory:
/usr/lib/firefox/plugins
/usr/lib/mozilla-firefox/plugins
~/.mozilla/plugins 

and in all these directoty I put the symbolic link 
libjavaplugin_oji.so

still in the test page if I try  which version of java my browser is using, it tells me
6_07!!

help

---

