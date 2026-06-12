---
title: "Limewire."
date: 2005-11-26
forum: General Help
---

### Post by cajunboy2k on 2005-11-26
Ok guys. I installed Lime Wire via Alien and the Unofficial Ubuntu guide, and no luck on either. I have the icon in my menu, but it will not launch. I'm at a loss. I also tried a search, but found no answer.

---

### Post by akiro.yamamoto on 2005-11-26
Did you create a .deb java file from the packaged .bin file from Sun's web site and install that debian file???.
Did you run this command to configure the version of java that will be used by default??
sudo update-alternatives --config java
 Post back here with the output of "
java -v"
Regards.

---

### Post by cajunboy2k on 2005-11-27
Thnks for the reply, but it's kinda greek to me.  In the pic below, which Java thing do I download? Also, could you point me to a site which explains how to make .deb file froom a .bin file?

Again, Thanks

---

### Post by cajunboy2k on 2005-11-27
Ok, I figured it out, all I did was to install the JAVA plugin for Mozilla/Firefox in the Adept package manager. It works great now.

---

### Post by noigeaR on 2005-11-27
There already are .deb packages of Sun Java available from [Ubuntu PLF]("http://wiki.ubuntu-fr.org/doc/plf")

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/pool/non-free/java/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/pool/non-free/java/)
Download the JRE (the smaller .deb) if you only need to run Java programs like limewire, download the SDK if you want to develop and compile Java programs yourself.
Once downloaded go to a terminal and type
```
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
```
or for the SDK version
```
sudo dpkg -i sun-j2sdk1.5_1.5.0+update05_i386.deb
```
after the package is installed type
```
sudo update-alternatives --config java
```
and press the number for the Sun Java you've just installed (should be the last number in the list).
To find out if Sun Java is now the standard Java on your system type
```
 java -version
```
This should show Java version 1.5.0_05

---

