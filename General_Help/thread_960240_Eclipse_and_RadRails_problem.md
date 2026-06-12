---
title: "Eclipse and RadRails problem"
date: 2008-10-27
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-10-27
Hi all.
I thought I might wanna get my hands a little dirty and learn some coding. Ruby on Rails was my choice. But I have a bit trouble getting it to work. Or more specifically getting Eclipse to work properly.

So, I installed according to some tutorials I read. But with Eclipse I ran into the following problem:
In one of the tutorials it said that after installing the RadRails plugin for Eclipse I need to configure the location of the interpreter. This is done in Eclipse in the menu: Window -> Preferences... -> Ruby -> Interpreters. However, in "Preferences" I don't have a category "Ruby". I checked the whole thing to not miss it since it might be hidden somewhere I thought. But no luck.
So, where should I do that?

I installed RadRails according to this: [http://update.aptana.com/update/studio/3.2/](http://update.aptana.com/update/studio/3.2/) (Installing Aptana Studio as a Plugin for Eclipse)

The other problem I have is, when I close Eclipse it basically freezes and I have to kill the app. After killing it a window with some info appears. See attached screeny for that. I guess that shouldn't work exactly like that... :D
But should I do about that?

When I start Eclipse from the console I get the following output:
> searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found    
2008-10-27 21:06:18.973::INFO:  Logging to STDERR via org.mortbay.log.StdErrLog
2008-10-27 21:06:19.291::INFO:  jetty-6.1.11                                   
2008-10-27 21:06:19.438::INFO:  Started SocketConnector@127.0.0.1:8500         
2008-10-27 21:06:19.439::INFO:  Started SocketConnector@127.0.0.1:8600         
2008-10-27 21:06:20.962::INFO:  jetty-6.1.11                                   
2008-10-27 21:06:20.011::INFO:  Opened /tmp/jetty_preview_server.log           
2008-10-27 21:06:20.050::INFO:  Started SocketConnector@127.0.0.1:8000         
2008-10-27 21:06:20.091::INFO:  jetty-6.1.11                                   
2008-10-27 21:06:20.033::INFO:  Started SocketConnector@127.0.0.1:8300
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]
(Build 1.2.0.018620_200810210145) [ERROR] Unable to disable feature
java.lang.Exception: There are no configured features with id com.aptana.ide.feature.professional
        at org.eclipse.update.standalone.DisableCommand.<init>(DisableCommand.java:74)
        at com.aptana.ide.professional.licensing.LicensingActivator.disableFeature(LicensingActivator.java:65)
        at com.aptana.ide.professional.licensing.TrialKey.disableProfessional(TrialKey.java:180)
        at com.aptana.ide.professional.licensing.TrialKey.earlyStartup(TrialKey.java:110)
        at org.eclipse.ui.internal.EarlyStartupRunnable.runEarlyStartup(EarlyStartupRunnable.java:87)
        at org.eclipse.ui.internal.EarlyStartupRunnable.run(EarlyStartupRunnable.java:66)
        at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
        at org.eclipse.ui.internal.Workbench$20.run(Workbench.java:1775)
        at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
(Build 1.2.0.018629) [ERROR] Invalid key
java.security.InvalidKeyException: Invalid AES key length: 26 bytes
        at com.sun.crypto.provider.AESCipher.engineGetKeySize(DashoA13*..)
        at javax.crypto.Cipher.b(DashoA13*..)
        at javax.crypto.Cipher.a(DashoA13*..)
        at javax.crypto.Cipher.a(DashoA13*..)
        at javax.crypto.Cipher.a(DashoA13*..)
        at javax.crypto.Cipher.init(DashoA13*..)
        at javax.crypto.Cipher.init(DashoA13*..)
        at com.aptana.ide.core.AptanaAuthenticator.decrypt(AptanaAuthenticator.java:325)
        at com.aptana.ide.core.AptanaAuthenticator.getPassword(AptanaAuthenticator.java:558)
        at com.aptana.ide.core.AptanaAuthenticator.getCachedAuthentication(AptanaAuthenticator.java:505)
        at com.aptana.ide.core.ui.CoreUIUtils.getEncryptedProValue(CoreUIUtils.java:2029)
        at com.aptana.ide.core.ui.update.SchedulerStartup.updateAnonymousId(SchedulerStartup.java:268)
        at com.aptana.ide.core.ui.update.SchedulerStartup.startSearch(SchedulerStartup.java:178)
        at com.aptana.ide.core.ui.update.SchedulerStartup.scheduleUpdateJob(SchedulerStartup.java:116)
        at com.aptana.ide.core.ui.update.SchedulerStartup.earlyStartup(SchedulerStartup.java:80)
        at org.eclipse.ui.internal.EarlyStartupRunnable.runEarlyStartup(EarlyStartupRunnable.java:87)
        at org.eclipse.ui.internal.EarlyStartupRunnable.run(EarlyStartupRunnable.java:66)
        at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
        at org.eclipse.ui.internal.Workbench$20.run(Workbench.java:1775)
        at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)


Just for the record, earlier it started like that:
> searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found    
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension                            
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension                       
    chown root:staff /usr/local/lib/eclipse/.eclipseextension                 
2008-10-27 20:55:43.218::INFO:  Logging to STDERR via org.mortbay.log.StdErrLog
2008-10-27 20:55:45.712::INFO:  jetty-6.1.11  
etc
etc
etc                                 

I ran these suggested commands and that issue seems to be resolved. At least it doesn't show up anymore when starting from console.

Some system info:
Kubuntu 8.04 w/ KDE 4.1
Eclipse 3.2
> gem -v
1.3.0

rails -v
Rails 2.1.2

ruby -v
ruby 1.8.6 (2007-09-24 patchlevel 111) [i486-linux]

java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

Any help would be appreciated.

---

### Post by Linux&amp;Gsus on 2008-10-28
Not mean to bump my own thread. :oops:
But is there anyone who knows what to do with that issue?

Cheers.

---

### Post by skotos on 2008-11-18
Unfortunately, I do not know Ruby but I would suggest you to download Pulse at [http://www.poweredbypulse.com/](http://www.poweredbypulse.com/) Pulse provides - under the voice "languages" - the Ruby Development Tools that - as for the other packages - should work out of the box. As a first try I would simply install that all alone and, later, add the other plugins I am interested on.  HTH

---

