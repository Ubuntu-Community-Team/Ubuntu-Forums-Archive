---
title: "Installing Aptana Studio in Hardy"
date: 2008-09-11
forum: General Help
---

### Post by notanxious on 2008-09-11
First of all, thanks in advance to all help that I will receive in this forum!!! 

I like many other am attempting to install Aptana Studio in Hardy. I managed to follow the instuctions given on [http://jasonleveille.com/2008/05/installing-aptana-on-ubuntu-804/](http://jasonleveille.com/2008/05/installing-aptana-on-ubuntu-804/) , but have still run into some problems. I will include the install instructions that I have followed thus far for your convenience.

# Install Java (sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts)
# Install Firefox 2 (sudo apt-get install firefox-2)
# Download and unzip aptana to /usr/local/aptana
# Save the following script as runAptana.sh to /usr/local/aptana
#!/bin/bash
export MOZILLA_FIVE_HOME=/usr/lib/firefox
/usr/local/aptana/AptanaStudio
# Make runAptana.sh executable (sudo chmod a+x runAptana.sh)
# Create a desktop launcher for Aptana and point it at runAptana.sh

    * Right click on your desktop
    * Click on Create Launcher
    * Name: Aptana
    * Command: browse for runAptana.sh

I encountered a problem when attempting to install the sun-java6-plugin...

"Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate"

This may very well be the root of my problem. However, I attempted to continue the install despite the previous error... Upon executing the runscript I get an error pointing me to a log file... And the error reads!

!MESSAGE Bundle [email]update@plugins/com.aptana.ide.xul_1.0.0.015414.jar[/email] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-09-11 20:58:58.997
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2008-09-11 20:58:58.998
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-09-11 20:58:58.998
!MESSAGE Bundle [email]update@plugins/com.aptana.ide.xul_1.0.0.015414.jar[/email] [77] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-09-11 20:58:58.998
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.
!SESSION 2008-09-11 21:00:21.500 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.osgi 4 0 2008-09-11 21:00:22.578
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/anxiety/Packages/aptana/configuration/org.eclipse.osgi/bundles/13/1/.cp/libswt-pi-gtk-3236.so: /home/anxiety/Packages/aptana/configuration/org.eclipse.osgi/bundles/13/1/.cp/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
	at com.aptana.ide.rcp.Application.run(Application.java:43)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2008-09-11 21:00:22.619
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-09-11 21:00:22.619
!MESSAGE Bundle [email]update@plugins/com.aptana.ide.xul_1.0.0.015414.jar[/email] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-09-11 21:00:22.619
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2008-09-11 21:00:22.620
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-09-11 21:00:22.620
!MESSAGE Bundle [email]update@plugins/com.aptana.ide.xul_1.0.0.015414.jar[/email] [77] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-09-11 21:00:22.620
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.


Your assistance in resolving this issue will be greatly appreciated. 

Signing off! 

THanks again!

---

### Post by deanmoore on 2008-10-19
I have same exact error.  Got an open-source Java installed, but (alas ...) not good enough for everything.

Having swore at this awhile, have developed private theories ... are you running a Core 2 Duo?  I'm running a brand-new duo-core from Los Alamos computers, ([http://laclinux.com/en/Laptop](http://laclinux.com/en/Laptop)), a Thinkpad.

According to < [http://ubuntuforums.org/archive/index.php/t-896983.html](http://ubuntuforums.org/archive/index.php/t-896983.html) >, AMD64 processors are a hassle.  What processor?

Unsure.  What you running?

---

