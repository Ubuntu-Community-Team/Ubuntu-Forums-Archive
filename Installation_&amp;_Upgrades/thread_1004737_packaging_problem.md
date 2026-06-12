---
title: "packaging problem"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by balat on 2008-12-07
Hi,

I have some problems with sun-java6-jre package. It seems to be broken :(

I have tried [http://sudan.ubuntuforums.com/showthread.php?p=6227043](http://sudan.ubuntuforums.com/showthread.php?p=6227043)
but it didn't helped:

[INDENT]amilo:/var/mail# dpkg --configure -a
amilo:/var/mail# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
E: The package sun-java6-jre needs to be reinstalled, but I can't find an archive for it.[/INDENT]

I tried to remove 

[INDENT]
amilo:/var/mail# dpkg -D7 -r sun-java6-jre
D000001: deferred_remove package sun-java6-jre
D000001: checking dependencies for remove `sun-java6-jre'
dpkg: error processing sun-java6-jre (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java6-jre
[/INDENT]

I can neither install

[INDENT]
amilo:/var/mail# dpkg -D7 -i sun-java6-jre
dpkg: error processing sun-java6-jre (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-java6-jre
[/INDENT]

Should I edit the package list? Where to find it?

Any idea please?

---

### Post by taurus on 2008-12-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by balat on 2008-12-07
You have caught me ...

[COLOR="Blue"]amilo:/var/mail# cat /etc/apt/sources.list
#
# deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 DVD Binary-1 20070407-11:40]/ etch contrib main


deb file:/mnt/debian1 etch main contrib

deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) etch main contrib non-free

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
[/COLOR]

actually I have Debian but I thaught the problem is not specific. Is it?

---

