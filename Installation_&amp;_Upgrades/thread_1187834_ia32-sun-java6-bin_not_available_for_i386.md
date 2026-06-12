---
title: "ia32-sun-java6-bin not available for i386"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by asmii on 2009-06-15
Hi All,

In the process of installing java6 on my freshly installed ubuntu 9.04 system, I was asked to install a package called ia32-sun-java6-bin, but couldn't find such a package for i386 based systems.

What I found was the same package for 64-bit machines.

Is there any alternative foe the same?

Please let me know.

-Asmii

---

### Post by asmii on 2009-06-15
The fact is that the packages sun-java6-bin_6-14-1_i386.deb and sun-java6-jre_6-14-1_all.deb are showing dependency on each other. 

In addition,  sun-java6-jre_6-14-1_all.deb is showing dependency on ia32-sun-java6-bin (ORed with sun-java6-bin_6-14-1_i386.deb) and that's precisely the reason why I was trying to install ia32-sun-java6-bin but sadly I found none for i386 platform.

Here is the screenshot for the same.

root@asmii-ubuntu:~/software/apache_ds# dpkg -i sun-java6-bin_6-14-1_i386.deb
(Reading database ... 111352 files and directories currently installed.)
Preparing to replace sun-java6-bin 6-14-1 (using sun-java6-bin_6-14-1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
dpkg: dependency problems prevent configuration of sun-java6-bin:
 [COLOR=Red]sun-java6-bin depends on sun-java6-jre (= 6-14-1); however:
  Package sun-java6-jre is not configured yet.[/COLOR]
dpkg: error processing sun-java6-bin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin


root@asmii-ubuntu:~/software/apache_ds# dpkg -i sun-java6-jre_6-14-1_all.deb
(Reading database ... 111352 files and directories currently installed.)
Preparing to replace sun-java6-jre 6-14-1 (using sun-java6-jre_6-14-1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-jre ...
dpkg: dependency problems prevent configuration of sun-java6-jre:
 [COLOR=Red]sun-java6-jre depends on sun-java6-bin (= 6-14-1) | ia32-sun-java6-bin (= 6-14-1); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.[/COLOR]
dpkg: error processing sun-java6-jre (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 sun-java6-jre


Please suggest................

-Asmii

---

