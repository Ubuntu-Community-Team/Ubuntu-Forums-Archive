---
title: "IDL: Fatal error initializing DML"
date: 2008-07-15
forum: General Help
---

### Post by DBMEboy on 2008-07-15
I recently installed IDL 7.  It seems to run from command line without any trouble, but if I try to open the gui I get the following error:

Fatal Error Initializing DML

Details:
Fatal error initializing DML
    
  Configuration info 
     IDL : /home/brown192/Desktop/IDL/idl70/idlde/../bin/bin.linux.x86 (Use default IDL)
     BML : /home/brown192/Desktop/IDL/idl70/idlde/bin.linux.x86 (Use default IDL)
     DML : /home/brown192/Desktop/IDL/idl70/idlde/bin.linux.x86 (Use default IDL)
     JDML: /home/brown192/Desktop/IDL/idl70/idlde/bin.linux.x86 (Use default IDL)
   
  com.rsi.jdml.LibraryLoadException: Failed to load idl_jdml from /home/brown192/Desktop/IDL/idl70/idlde/bin.linux.x86
     at com.rsi.jdml.PlatformSupport.loadNeededLibrary(PlatformSupport.java:170)
     at com.rsi.jdml.PlatformSupport.loadLibraries(PlatformSupport.java:371)
     at com.rsi.jdml.DMLAccess.initializeDML(DMLAccess.java:178)
     at com.rsi.idldt.core.IDLProcessManager.initializeDML(IDLProcessManager.java:236)
     at com.rsi.idldt.core.IDLProcessManager.createIDLProcess(IDLProcessManager.java:105)
     at com.rsi.idldt.core.IDLDTCorePlugin$PostCoreBundleStartJob.run(IDLDTCorePlugin.java:242)
     at org.eclipse.core.internal.jobs.Worker.run(Worker.java:55)
  Caused by: java.lang.UnsatisfiedLinkError: /home/brown192/Desktop/IDL/idl70/idlde/bin.linux.x86/libidl_jdml.so: libidl_dml.so: cannot open shared object file: No such file or directory
     at java.lang.Runtime._load(libgcj.so.81)
     at java.lang.Runtime.load(libgcj.so.81)
     at java.lang.System.load(libgcj.so.81)
     at com.rsi.jdml.PlatformSupport.loadExplicitLibrary(PlatformSupport.java:127)
     at com.rsi.jdml.PlatformSupport.loadNeededLibrary(PlatformSupport.java:161)
     ...6 more

I'm running Ubuntu 8.04.  Any ideas?

---

### Post by flayedone on 2008-07-25
Hi there,

I had this problem a while back and recently I have gotten a new computer that I needed IDL 7.0 on, well I had this problem again.

Open up Synaptic Package Manager
do a search for libstdc++
install libstdc++5
Then it should work

I found this on a, I believe, Chinese forum a while back:

[http://foxmulder.blog.sohu.com/73128880.html](http://foxmulder.blog.sohu.com/73128880.html)

You probably want to get google to translate it.

I hope this gets it to work for you :)

---

