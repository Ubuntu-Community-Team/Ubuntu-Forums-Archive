---
title: "java problem"
date: 2008-09-14
forum: General Help
---

### Post by ubunutulearner72 on 2008-09-14
hi all. i was trying to install a program and received a java error: 

'Starting Installer ...
java.lang.NullPointerException
   at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
   at com.install4j.runtime.Launcher.main(Unknown Source)
java.lang.NullPointerException

retreiving information about the java version in terminal returned:

user@user:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: version not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)
stef@stef-laptop:~$ 

I am unsure of how to proceed and was wondering if anyone could help?

---

### Post by Tanker Bob on 2008-09-14
Please see my reply on [this thread](http://ubuntuforums.org/showpost.php?p=5790311&postcount=5).

---

