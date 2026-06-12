---
title: "Unmet dependencies after installing eclipse 3.4 from PPA"
date: 2008-09-13
forum: General Help
---

### Post by gasull on 2008-09-13
Hi.

I installed eclipse 3.4 [from PPA]("https://launchpad.net/~rockwalrus/+archive").  Eclipse works fine.  Azureus works fine too.  But I get this error when I try to install anything with aptitude:
```

The following packages have unmet dependencies:
  eclipse-gcj: Depends: libswt3.4-gtk-gcj which is a virtual package.
  eclipse-jdt-gcj: Depends: eclipse-jdt (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
  azureus: Depends: libswt3.2-gtk-java but it is not installable
  eclipse-pde-gcj: Depends: eclipse-pde (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
  eclipse-platform-gcj: Depends: eclipse-platform (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
  libswt3.2-gtk-gcj: Depends: libswt3.2-gtk-java (= 3.2.2-5ubuntu2) but it is not installable
  eclipse-rcp-gcj: Depends: eclipse-rcp (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libswt3.4-gtk-java

Install the following packages:
libswt3.2-gtk-java [3.2.2-5ubuntu2 (hardy)]
```

I don't want to switch from libswt3.4-gtk-java to libswt3.2-gtk-java, because I need it for eclipse 3.4.

What can I do so I can use aptitude and still keep the new eclipse?

TIA.

---

### Post by icheyne on 2008-09-13
Is anything else obviously broken? If not, how about:

```
sudo aptitude hold libswt3.4-gtk-java
```

---

### Post by gasull on 2008-09-13
I just did it, but now I get this error:

```
The following packages are BROKEN:
  azureus eclipse-gcj eclipse-jdt-gcj eclipse-pde-gcj eclipse-platform-gcj eclipse-rcp-gcj libswt3.2-gtk-gcj 
The following packages are unused and will be REMOVED:
  libcommons-beanutils-java libcommons-collections-java libcommons-collections3-java libcommons-dbcp-java 
  libcommons-digester-java libcommons-el-java libcommons-launcher-java libcommons-logging-java libcommons-modeler-java 
  libcommons-pool-java libjsch-java libservlet2.3-java libservlet2.4-java libswt3.2-gtk-jni libtomcat5.5-java 
The following packages have been kept back:
  awn-core-applets-bzr 
0 packages upgraded, 0 newly installed, 15 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 16.4MB will be freed.
The following packages have unmet dependencies:
  eclipse-gcj: Depends: libswt3.4-gtk-gcj which is a virtual package.
  eclipse-jdt-gcj: Depends: eclipse-jdt (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
  azureus: Depends: libswt3.2-gtk-java but it is not installable
  eclipse-pde-gcj: Depends: eclipse-pde (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
  eclipse-platform-gcj: Depends: eclipse-platform (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
  libswt3.2-gtk-gcj: Depends: libswt3.2-gtk-java (= 3.2.2-5ubuntu2) but it is not installable
  eclipse-rcp-gcj: Depends: eclipse-rcp (= 3.2.2-5ubuntu2) but 3.4.0-0ubuntu1~ppa8 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
azureus
eclipse-gcj
eclipse-jdt-gcj
eclipse-pde-gcj
eclipse-platform-gcj
eclipse-rcp-gcj
libswt3.2-gtk-gcj

Leave the following dependencies unresolved:
eclipse recommends eclipse-gcj
eclipse-pde recommends eclipse-pde-gcj
eclipse-jdt recommends eclipse-jdt-gcj
eclipse-platform recommends eclipse-platform-gcj
eclipse-rcp recommends eclipse-rcp-gcj
Score is -2627

Accept this solution? [Y/n/q/?] 
```

Should I run aptitude hold on all the packages that are shown as broken? --They are not broken, because they do work.

Thanks.

---

### Post by gasull on 2008-09-14
Solved just removing eclipse-gcj.  I don't need it because I'm using IBM's Java.  You won't need it either if you use Sun's Java.

---

