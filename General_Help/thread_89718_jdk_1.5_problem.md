---
title: "jdk 1.5 problem"
date: 2005-11-13
forum: General Help
---

### Post by btumpps on 2005-11-13
hi. i have installed jdk 1.5 to the directory "/opt/jdk" but i cannot set the execution path. and so, when i type for example "java -version" on the console i get the response:

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

i want to set the execution path "/opt/jdk/bin", i dont want to use the GNU libgjc. how can i do that?

and also i want my java apps to use the jvm of jdk 1.5.0 instead of using GNU libgjc.

thanks in advance

---

### Post by nszabolcs on 2005-11-13
```

sudo ln -sf /opt/jdk/bin/java_vm /usr/bin/java_vm
sudo update-alternatives --install /usr/bin/java java /opt/jdk/bin/java 1

```

for details, removal and firefox plugin see: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)

---

### Post by angkor on 2005-11-28
[QUOTE=nszabolcs]```

sudo ln -sf /opt/jdk/bin/java_vm /usr/bin/java_vm
sudo update-alternatives --install /usr/bin/java java /opt/jdk/bin/java 1

```

for details, removal and firefox plugin see: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)[/QUOTE]

Just dropped in to let other people know the above method worked perfectly for me when I tried to install JAlbum on Breezy.

Without the update-alternatives method Ubuntu kept using an older version and JAlbum gave the following error msg: (for people googling the message;))

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)

Thanx nszabolcs!

---

