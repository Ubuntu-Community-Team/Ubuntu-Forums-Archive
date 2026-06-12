---
title: "Error when installing packages"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Ludachrispeed on 2009-02-08
Every time I try to install a package with Synaptic, I get this error in a dialog box:

```
E: libxine1-bin: package libxine1-bin is not ready for configuration
```

I tried running  dpkg --configure -a  but then I got this error message:

```
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
```

It seems like all my packages are getting installed, but the error is disconcerting nonetheless.  Does anybody know how to fix this?

Thanks very much! All help is appreciated!

---

### Post by zvacet on 2009-02-08
Did you run 

```
sudo dpkg --configure -a
```

and you can try this one 

```
sudo apt-get -f install
```

---

### Post by Ludachrispeed on 2009-02-08
Thanks for the amazingly quick reply!

I have tried ```
sudo dpkg --configure -a
```

and it didn't work.  I just tried ```
sudo apt-get -f install
```

and this is what I got:

```
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libcommons-collections3-java gappletviewer-4.3 junit4 libcommons-pool-java
  gnuchess-book libavutil1d libgcj8-1 debhelper libgcj9-0 ttf-wqy-zenhei libgcj-bc
  mobile-broadband-provider-info intltool-debian vorbis-tools liblucene-java libmbca0
  libcommons-el-java antlr id3v2 junit ttf-kannada-fonts libregexp-java liblog4j1.2-java
  po-debconf libpostproc1d libantlr-java libgcj8-jar libswt3.2-gtk-java libservlet2.4-java
  libaccess-bridge-java exuberant-ctags libmail-sendmail-perl gij-4.2 gij-4.3 libbcel-java
  gettext ant libcommons-launcher-java libcommons-logging-java default-jdk gcj-4.2-base
  default-jre libgcj-common gjdoc ttf-telugu-fonts libjaxp1.3-java openjdk-6-jre-headless
  openjdk-6-jdk tzdata-java java-gcj-compat-headless libxul0d openjdk-6-jre libgcj8-1-awt
  openjdk-6-jre-lib libcommons-dbcp-java libgcj9-jar libxerces2-java java-gcj-compat
  libcommons-collections-java libtimedate-perl dpkg-dev libgcj9-0-awt fastjar rhino
  ttf-oriya-fonts libboost-filesystem1.34.1 libswt3.2-gtk-gcj html2text xaw3dg
  libservlet2.3-java liblucene-java-doc default-jre-headless libxul-common gnuchess
  libjsch-java libswt3.2-gtk-jni ca-certificates-java ttf-bengali-fonts ant-optional
  libid3-3.8.3c2a libantlr-java-gcj libsys-hostname-long-perl libmx4j-java build-essential
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing libxine1-bin (--configure):
 package libxine1-bin is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

I suppose that last line has to do with the problem!  Any ideas?

Thank again.

---

### Post by Ludachrispeed on 2009-02-08
Okay I think I fixed it -- I just removed the problem packages (everything with the name libxine1, and gxine)

It's just some package that has to do with playing media... probably something I installed during the not-so-trivial task of trying to make ubuntu play a DVD!

Thank again!

---

