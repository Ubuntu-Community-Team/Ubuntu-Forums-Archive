---
title: "problem installing JAlbum"
date: 2005-11-15
forum: General Help
---

### Post by sbaush on 2005-11-15
I downloaded the installer from [JAlbum Download page ]("http://jalbum.net/download3.jsp")
I type in terminal ```
sudo sh JAlbuminstall.bin

```
But this is the answer... ```
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError: while resolving class: ZeroGe
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at ZeroGd.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at com.zerog.ia.installer.LifeCycleManager.a(boolean) (Unknown Source)
   at com.zerog.ia.installer.LifeCycleManager.b(java.lang.String[]) (Unknown Source)
   at com.zerog.ia.installer.LifeCycleManager.a(java.lang.String[]) (Unknown Source)
   at com.zerog.ia.installer.Main.main(java.lang.String[]) (Unknown Source)
   at java.lang.reflect.Method.invoke(java.lang.Object, java.lang.Object[]) (/usr/lib/libgcj.so.6.0.0)
   at com.zerog.lax.LAX.launch() (Unknown Source)
   at com.zerog.lax.LAX.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: com.apple.mrj.MRJOSType not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/tmp/install.dir.10088/InstallerData/,file:./,file:/tmp/install.dir.10088/InstallerData/installer.zip,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   ...13 more
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

```

What can I do?

Java is installed on my pc: 
```
VERIFY YOUR JAVA SOFTWARE INSTALLATION

We detected your Java environment as follows;
Description 	Your Environment
Java Runtime Vendor:
	
Sun Microsystems Inc.
Java Runtime Version
	
1.5.0_05
 

CONGRATULATIONS, you have the Latest version of Java!
```

I need help...

THANKS!!

---

### Post by Wally68 on 2005-11-15
I don't know java at all, but I did download and install JAlbum without any problems.

```
Caused by: java.lang.ClassNotFoundException: com.apple.mrj.MRJOSType not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/tmp/install.dir.10088/InstallerData/,file:./,file:/tmp/install.dir.10088/InstallerData/installer.zip,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
```

Are you sure you didn't download the apple version? It's right above the linux version.

---

### Post by sbaush on 2005-11-15
I try to download another .bin but this make the same error!!!
Some ideas??
I need JAlbum!!!

Thanks to all!

---

### Post by sbaush on 2005-11-15
Now i have reinstalled java and it runs...
Thanks...

---

### Post by luxir on 2005-11-18
I get the same error. Re-installed sun-j2re1.5, but no success.
Then tried sun-j2sdk1.5, but that did not help. :(

---

### Post by sbaush on 2005-11-18
I have the correct use of JAlbum only with the old version, infact i heve reistalled this!!!

---

