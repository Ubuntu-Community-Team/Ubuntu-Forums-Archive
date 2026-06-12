---
title: "[SOLVED] OpenJDK (and Netbeans)"
date: 2008-08-13
forum: General Help
---

### Post by Jesdisciple on 2008-08-13
```
Err http://us.archive.ubuntu.com hardy-updates/universe tzdata-java 2008c-1ubuntu0.8.04
  404 Not Found [IP: 91.189.88.46 80]                        
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tzdata/tzdata-java_2008c-1ubuntu0.8.04_all.deb  404 Not Found [IP: 91.189.88.46 80]
```Whenever I tell apt-get to install OpenJDK (indirectly via Netbeans), I get that partial output.  Can I get around it?

Thanks!

---

### Post by Sinkingships7 on 2008-08-13
You could install the bundle package from the Java site.

[http://java.sun.com/javase/downloads/netbeans.html](http://java.sun.com/javase/downloads/netbeans.html)

That's what I did and it works great. Update 7 (Java) and 6.1 (NetBeans). Both of those are more up to date than the repo versions.

---

### Post by Nepherte on 2008-08-13
Just change your software repositories to another mirror, refresh and try installing it again.

---

### Post by dexter.deepak on 2008-08-13
is this problem limited to openjdk or extends to other programs too ?
have you tried changing the location of download server in the system -> admin->software-sources ?

---

### Post by Jesdisciple on 2008-08-13
> **Sinkingships7 said:**
> You could install the bundle package from the Java site.

[http://java.sun.com/javase/downloads/netbeans.html](http://java.sun.com/javase/downloads/netbeans.html)

That's what I did and it works great. Update 7 (Java) and 6.1 (NetBeans). Both of those are more up to date than the repo versions.Wouldn't that give me Sun's Java?

I was considering trying that for OpenJDK, but the repo makes updates automatic, and I know I'll never think to check for them.  Apart from apt, I normally find out about updates from some offhand comment someone makes - or a page I visit for some special reason.

> **Nepherte said:**
> Just change your software repositories to another mirror, refresh and try installing it again.The newbie (I) was about to ask how to do that but got the answer from Dexter.

> **dexter.deepak said:**
> is this problem limited to openjdk or extends to other programs too ?I haven't noticed it with anything else, so I don't think it's a mirror-wide problem.  And I'm updating everything on the main server right now (because I had to update the package info to change mirrors), so it's not my computer.

> **dexter.deepak said:**
> have you tried changing the location of download server in the system -> admin->software-sources ?*waits to complete the installation*  The main server has the missing package.  :)  *switches back to the US server*

Umm...```
update-binfmts: warning: current package is openjdk-6, but binary format already installed by sun-java6
```Does that mean I somehow got the proprietary Java?  How?  EDIT:```
$ sudo apt-get remove sun-java6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6
```

---

### Post by Nepherte on 2008-08-14
The package name is sun-java6-jre.

The warning you get is probablly because the default java virtual machine is sun's and not the openjdk one. You can change that as follows:
```
sudo update-alternatives --config java
```

---

### Post by Jesdisciple on 2008-08-14
Many thanks to all of you!

---

### Post by Jesdisciple on 2008-08-17
Yes, this thread was marked as solved...  Netbeans still won't run; I just assumed it would earlier.```
$ netbeans
Cannot find java. Please use the --jdkhome switch.
```I have openjdk-6-jdk and its 3 openjdk dependencies installed, according to Synaptic.

EDIT: [http://ubuntune.blogspot.com/2008/05/desktop-cube-netbeans-install.html](http://ubuntune.blogspot.com/2008/05/desktop-cube-netbeans-install.html)  Now how can I make that the default?

---

### Post by Nepherte on 2008-08-17
Maybe there's a configuration file under /etc named something like netbeans.conf where you could set it. Just logical speculation as I don't have netbeans.

---

### Post by Jesdisciple on 2008-08-17
You're right!
(current version)```
# Default location of JDK, can be overridden by using --jdkhome <dir>:
netbeans_jdkhome="/usr/lib/jvm/java-6-openjdk"
```

But Netbeans gives a runtime warning:```
$ netbeans --jdkhome /usr/lib/jvm/java-6-openjdk
Aug 17, 2008 8:39:49 AM com.sun.corba.se.impl.ior.IORImpl getProfile
WARNING: "IOP00511201: (INV_OBJREF) IOR must have at least one IIOP profile"
org.omg.CORBA.INV_OBJREF:   vmcid: SUN  minor code: 1201  completed: No
	at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:473)
	at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:495)
	at com.sun.corba.se.impl.ior.IORImpl.getProfile(IORImpl.java:334)
	at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:787)
	at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:761)
	at com.sun.corba.se.impl.encoding.CDRInputStream.read_Object(CDRInputStream.java:231)
	at com.sun.corba.se.impl.resolver.INSURLOperationImpl.getIORFromString(INSURLOperationImpl.java:116)
	at com.sun.corba.se.impl.resolver.INSURLOperationImpl.operate(INSURLOperationImpl.java:126)
	at com.sun.corba.se.impl.orb.ORBImpl.string_to_object(ORBImpl.java:838)
	at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
	at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1058)
	at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:341)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:786)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:874)
	at sun.swing.SwingUtilities2$AATextInfo.getAATextInfo(SwingUtilities2.java:131)
	at javax.swing.plaf.metal.MetalLookAndFeel.initComponentDefaults(MetalLookAndFeel.java:1564)
	at javax.swing.plaf.basic.BasicLookAndFeel.getDefaults(BasicLookAndFeel.java:147)
	at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1599)
	at javax.swing.UIManager.setLookAndFeel(UIManager.java:545)
	at javax.swing.UIManager.setLookAndFeel(UIManager.java:585)
	at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1334)
	at javax.swing.UIManager.initialize(UIManager.java:1421)
	at javax.swing.UIManager.maybeInitialize(UIManager.java:1409)
	at javax.swing.UIManager.getUI(UIManager.java:1006)
	at javax.swing.JPanel.updateUI(JPanel.java:126)
	at javax.swing.JPanel.<init>(JPanel.java:86)
	at javax.swing.JPanel.<init>(JPanel.java:109)
	at javax.swing.JPanel.<init>(JPanel.java:117)
	at org.netbeans.updater.UpdaterFrame.<init>(Unknown Source)
	at org.netbeans.updater.UpdaterFrame.main(Unknown Source)

```Since it's a GNOME thing, does anyone have an idea?

---

### Post by txcrackers on 2008-08-17
Suggestion: don't use OpenJDK, use the Sun JDK. OpenJDK isn't fully "baked" yet.

---

### Post by Jesdisciple on 2008-08-17
I have reluctantly done so.

Thanks!

---

### Post by fenT1 on 2008-08-18
use my signature

---

