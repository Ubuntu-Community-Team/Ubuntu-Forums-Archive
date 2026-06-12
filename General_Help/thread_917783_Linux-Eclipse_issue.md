---
title: "Linux-Eclipse issue"
date: 2008-09-12
forum: General Help
---

### Post by mrwasabi on 2008-09-12
Linux-eclipse problem?
i have found the following problem on running eclipse


JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib...
-Dgnu.gcj.runtime.VMClassLoader.librar...
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 34800f
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib...
-Dgnu.gcj.runtime.VMClassLoader.librar...
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---

### Post by Nepherte on 2008-09-12
Removing ~./eclipse/ should allow you to start eclipse again.

---

