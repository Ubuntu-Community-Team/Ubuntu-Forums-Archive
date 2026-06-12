---
title: "No panel, no anything in ubuntu 8.10"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by jimijunk on 2008-12-06
HAve been using Ubuntu for four years or so on an HP a400y. Always have to include switches aspc=off noapic nolapic. This time when I upgraded to 8.10 I got nothing but black sreen with x pointer after boot. Figured I would wait and install  again later after bugs were removed. INstalled again complete, now after I login all I get is moving mouse pointer and nothing else but orange desktop. No menu and staut bar. I am essentially "locked out". PLease help!!! Oh GOd don't make me go back to MS Windows. Oh God! Oh God! Oh God!!!  No, No NO-o-o-o-o-oo-o-o-!!

---

### Post by Partyboi2 on 2008-12-08
When you get to the brown screen try pressing Ctl+Alt+F2 to get to a terminal and then remove compiz and compiz-core
```
sudo apt-get remove compiz compiz-core
``` 
[http://varunkashyap.wordpress.com/2008/11/05/ubuntu-freezes-with-blackorange-screen-on-boot-up-and-the-solution/](http://varunkashyap.wordpress.com/2008/11/05/ubuntu-freezes-with-blackorange-screen-on-boot-up-and-the-solution/)

---

