---
title: "ldconfig during postinst"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by jobano on 2009-03-27
hi,

I have a situation with the debian port of dellomsa (Dell OpenManage Server Administrator), available here: [[COLOR="Navy"]https://subtrac.sara.nl/oss/omsa_2_deb/wiki[/COLOR]](https://subtrac.sara.nl/oss/omsa_2_deb/wiki)

I already open [[COLOR="Navy"]a ticket on their trac[/COLOR]]("https://subtrac.sara.nl/oss/omsa_2_deb/ticket/36") but the problem appear to be specific Ubuntu.

For me, the problem comes from the use of ldconfig during the postinst script, I've made many tries: the newly added libraries, added by postinst into /etc/ld.so.conf.d/dell-omsa.conf, are not loaded into ldconfig and the service restart failed.
And just after leaving dpkg's scripts, the ldconfig cache have the new librairies and the restart is Ok.

Someone know something about an ldconfig/postinst specificity under Ubuntu ?

Note: that package install runs marvelously under a debian lenny

---

