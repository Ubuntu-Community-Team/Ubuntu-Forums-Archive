---
title: "Prevent Hardware Failure"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by leetcharmer on 2007-10-20
I'm not sure if my hardware is failing, but here are some things that tip me off:
[LIST=1]
[*]Can't make it through a single full Ubuntu install
[INDENT][LIST]
[*]via CD
[*]via Network Install
[/LIST][/INDENT]
[*]Missing Hard drive (during POST)
[*]Downloads typically fail checksum[/LIST]

Is there a way to have ubuntu check my hard drives to prevent a need for replacing it?  Or is there a way to check to make sure any other hardware I have is in proper conditions?  I don't want to have to spend money if at all possible.

Bonus: It seems that no matter what medium I use to get Ubuntu on the machine in question, failure always arises when it comes to Openoffice.org or Java being installed.

By the way, right now I'm trying to install edubuntu via a clean cli install.  sudo apt-get install edubuntu-desktop now errors out due to openoffice.org error codes:
> : Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas how to continue the installation?

Thanks!

---

### Post by leetcharmer on 2007-10-20
An error occured:

```
E: gij-4.2: subprocess post-installation script returned error exit status 2
E: gij: dependency problems - leaving unconfigured
E: libjline-java: dependency problems - leaving unconfigured
E: bsh: dependency problems - leaving unconfigured
E: libservlet2.4-java: dependency problems - leaving unconfigured
E: libhsqldb-java: dependency problems - leaving unconfigured
E: libjaxp1.3-java: dependency problems - leaving unconfigured
E: libxerces2-java: dependency problems - leaving unconfigured
E: libxalan2-java: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
```

Terminal output:
```
Setting up gij-4.2 (4.2.1-5ubuntu5) ...
gcj-dbtool-4.2: symbol lookup error: /usr/lib/libgcj.so.81: undefined symbol: _ZN4java3awt5image13PixelGrabber6class$E
dpkg: error processing gij-4.2 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.2 (>= 4.2.1-5); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjline-java:
 libjline-java depends on gij | java-gcj-compat | java2-runtime | java1-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
dpkg: error processing libjline-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsh:
 bsh depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
 bsh depends on libjline-java; however:
  Package libjline-java is not configured yet.
dpkg: error processing bsh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.4-java:
 libservlet2.4-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
dpkg: error processing libservlet2.4-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on gij | java-gcj-compat | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
 libhsqldb-java depends on libservlet2.4-java; however:
  Package libservlet2.4-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjaxp1.3-java:
 libjaxp1.3-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
dpkg: error processing libjaxp1.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxerces2-java:
 libxerces2-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
 libxerces2-java depends on libjaxp1.3-java; however:
  Package libjaxp1.3-java is not configured yet.
dpkg: error processing libxerces2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxalan2-java:
 libxalan2-java depends on libjaxp1.3-java; however:
  Package libjaxp1.3-java is not configured yet.
 libxalan2-java depends on libxerces2-java (>= 2.8.0); however:
  Package libxerces2-java is not configured yet.
dpkg: error processing libxalan2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on libxerces2-java; however:
  Package libxerces2-java is not configured yet.
 openoffice.org-java-common depends on libxalan2-java (>= 2.6.0-1); however:
  Package libxalan2-java is not configured yet.
 openoffice.org-java-common depends on bsh (>= 2.0b4-1); however:
  Package bsh is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on gij | java-gcj-compat | libgcj8-1-awt | sun-java5-jre | sun-java6-jre | icedtea-java7-jre | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package libgcj8-1-awt is not installed.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package icedtea-java7-jre is not installed.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
 openoffice.org-base depends on libhsqldb-java (>= 1.8.0.8-1); however:
  Package libhsqldb-java is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.2
 gij
 libjline-java
 bsh
 libservlet2.4-java
 libhsqldb-java
 libjaxp1.3-java
 libxerces2-java
 libxalan2-java
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gij-4.2 (4.2.1-5ubuntu5) ...
gcj-dbtool-4.2: symbol lookup error: /usr/lib/libgcj.so.81: undefined symbol: _ZN4java3awt5image13PixelGrabber6class$E
dpkg: error processing gij-4.2 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.2 (>= 4.2.1-5); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjaxp1.3-java:
 libjaxp1.3-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
dpkg: error processing libjaxp1.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjline-java:
 libjline-java depends on gij | java-gcj-compat | java2-runtime | java1-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
dpkg: error processing libjline-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on gij | java-gcj-compat | libgcj8-1-awt | sun-java5-jre | sun-java6-jre | icedtea-java7-jre | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package libgcj8-1-awt is not installed.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package icedtea-java7-jre is not installed.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.4-java:
 libservlet2.4-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
dpkg: error processing libservlet2.4-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxerces2-java:
 libxerces2-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
 libxerces2-java depends on libjaxp1.3-java; however:
  Package libjaxp1.3-java is not configured yet.
dpkg: error processing libxerces2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on gij | java-gcj-compat | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
 libhsqldb-java depends on libservlet2.4-java; however:
  Package libservlet2.4-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsh:
 bsh depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not installed.
  Package java1-runtime is not installed.
  Package gij which provides java1-runtime is not configured yet.
  Package gij-4.2 which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.2 which provides java2-runtime is not configured yet.
 bsh depends on libjline-java; however:
  Package libjline-java is not configured yet.
dpkg: error processing bsh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxalan2-java:
 libxalan2-java depends on libjaxp1.3-java; however:
  Package libjaxp1.3-java is not configured yet.
 libxalan2-java depends on libxerces2-java (>= 2.8.0); however:
  Package libxerces2-java is not configured yet.
dpkg: error processing libxalan2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on libxerces2-java; however:
  Package libxerces2-java is not configured yet.
 openoffice.org-java-common depends on libxalan2-java (>= 2.6.0-1); however:
  Package libxalan2-java is not configured yet.
 openoffice.org-java-common depends on bsh (>= 2.0b4-1); however:
  Package bsh is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured

```

---

