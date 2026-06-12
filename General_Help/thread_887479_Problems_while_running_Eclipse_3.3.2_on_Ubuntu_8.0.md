---
title: "Problems while running Eclipse 3.3.2 on Ubuntu 8.04"
date: 2008-08-12
forum: General Help
---

### Post by arunize on 2008-08-12
I have installed sun java 
```
install java : sudo aptitude install sun-java6-jdk

```

sudo update-java-alternatives --list

is showing

java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun

and 

java -version

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

I hope Java installation is perfect.

I downloaded Eclipse 
eclipse-SDK-3.3.2-linux-gtk.tar.gz from eclipse.org
and extracted in my home/opt/eclipse

while running eclipse i am getting ...
```
JVM terminated. Exit code=13
/usr/bin/java
-Xms40m
-Xmx256m
-jar /home/touchpoint/opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/touchpoint/opt/eclipse/eclipse
-name Eclipse
--launcher.library /home/touchpoint/opt/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.3.R33x_v20080118/eclipse_1023.so
-startup /home/touchpoint/opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-exitdata b800e
-vm /usr/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /home/touchpoint/opt/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar 

```

How to resolve this?

-arun

---

### Post by &lt;eMPy&gt; on 2008-09-09
Hi,

I expreienced the same problem too.
Seems to be a problem with the x86_64 version.
Installing the ia32-libs package helped a bit. I am experiencing other problems (like wrong eclipse version et. al.). However, the binaries do run now.

mfg

---

