---
title: "Can't install java common package"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-05-10
Hi guys, I have to install openoffice.org java-common-package according to Openoffice 3 to enable me to work with html. I can't for the life of me get the java common package installed.
I just tried an install from [http://mediakey.dk](http://mediakey.dk) as follows along with the resulting report in Terminal;
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fontsReading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

Also, when I try to add a repository such as [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty the Software Source 'add' in option just sits there as if I haven't completed the source path - which I probably havne't but, I don't know enough about the correct path to correct the mistake/s.
Your help as always is gratefully received.

---

### Post by dstew on 2009-05-10
I don't know if I can help you with everything, but at least that mirror URL I can help you:```
http://mirror.uni-c.dk/pub/ubuntu/dists/jaunty/
```I have Ubuntu 8.04, and the OpenOffice version here is 2.4. I do not know if version 3 works with 8.04, but I suspect not, because it is not in the Synaptic list. If a program is not in the list, it usually won't work if you download it directly, because the kernel version of the Ubuntu flavor will not support it.

As far as a Java run-time environment (jre), that should be installed by way of Synaptic. I have it in my list there. It is in the Multiverse repository, in the Libraries section.

---

