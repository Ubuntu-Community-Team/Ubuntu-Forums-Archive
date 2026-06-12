---
title: "Problem with Java: ClassNotFoundException"
date: 2005-12-06
forum: General Help
---

### Post by caspian on 2005-12-06
Ever since I upgraded to Breezy Badger, I can no longer run Java programs. I can compile with javac, but when I try to run the program using the "java" command, I get an error like this:

> 
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5ErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt8AWTErrorC1EPNS_4lang6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt7Toolkit17getDefaultToolkitEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3awt10EventQueue11invokeLaterEPNS_4lang8RunnableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing14SwingUtilities11invokeLaterEPN4java4lang8RunnableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing14RepaintManager19addInvalidComponentEPNS0_10JComponentE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing10JComponent10revalidateEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing10JComponent9setOpaqueEb (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing6JPanelC1EPN4java3awt13LayoutManagerEb (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing6JPanelC1Ev (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing9JRootPane15createGlassPaneEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing9JRootPane12getGlassPaneEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing9JRootPaneC1Ev (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing6JFrame14createRootPaneEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing6JFrame11getRootPaneEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing6JFrame9frameInitEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN5javax5swing6JFrameC1EPN4java4lang6StringE (/usr/lib/libgcj.so.6.0.0)
   at Days.main(java.lang.String[]) (Unknown Source)
   at ._ZN16_Jv_InterpMethod9run_classEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN3gnu4java4lang10MainThread9call_mainEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN3gnu4java4lang10MainThread3runEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_ThreadRunPN4java4lang6ThreadE (/usr/lib/libgcj.so.6.0.0)
   at ._Z11_Jv_RunMainP14_Jv_VMInitArgsPN4java4lang5ClassEPKciPS6_b (/usr/lib/libgcj.so.6.0.0)
   at .main (/usr/lib/libgij.so.6.0.0)
   at .__libc_start_main (/lib/tls/i686/cmov/libc-2.3.5.so)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java3net14URLClassLoader9findClassEPNS_4lang6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringEb (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class7forNameEPNS0_6StringEbPNS0_11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class7forNameEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   ...23 more


I tried reinstalling the JDK and JVM, but I still get the same problem. Anyone got an idea what's going on?

Thanks.

---

### Post by l.tambiah on 2005-12-06
I know there are many ways to install the jdk and jre. I usually install the jdk as it includes the runtime environment as well. As for your problem i dont have a clue, try removing your java related packages and reinstall. I know you have tried this, but you must try again, i have java running on my Ubuntu Breezy with no problems.

Use this wiki guide to install Java - [http://https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca]("http://https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca")


If you have any more problems after trying this let us know...

---

