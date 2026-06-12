---
title: "Java runtime env"
date: 2005-11-11
forum: General Help
---

### Post by edcolberg on 2005-11-11
I'm trying to use something in firefox that required java. It would not install the plugin automatically, so I went and downloaded it from sun. It was a .bin and I executed it and it made an RPM so I did an alien on it to get it to a .deb than I installed it with dpgk -i. After that I made a symlink to the mozilla plugins dir to the plugin but when I  try to use it in mozilla it does not work. Also when I try to execute java (in the JRE's bin directory) it says 

Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

Is there something else I need to complete the java install. Thanks.

---

### Post by 23meg on 2005-11-11
The instructions given [here]("http://www.ubuntuforums.org/showthread.php?t=76754") should help.

---

