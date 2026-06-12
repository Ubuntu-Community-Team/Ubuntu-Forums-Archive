---
title: "Facebook photo upload problem: &quot;publisher cannot be verified by trusted source&quot;"
date: 2008-10-28
forum: General Help
---

### Post by John RG on 2008-10-28
I'm still newish at all this, but I have spent a few hours trying various things off the forums. I am having no luck using the Facebook applet to upload photos. 

I have removed Icedtea, installed the latest version of sun-java6 and the plugin, I think I'm on 32 bit system. My system is up to date, and I have accessed all the repositories. It is times like this when I think all OSs have their problems. I love how stable & secure Ubuntu is, but it is scary when it gets this techie to try and fix things. But the forum is very supportive.

When trying to upload photos into Facebook, the applet comes up with an error which says "The publisher cannot be verified by a trusted source. Code will be treated as unsigned." The name says something about FacebookPhotoUploader5 and java.io.EOFException.  Firefox then crashes in an ugly fashion. 

When I click on details, I get this:
java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:375)
	at sun.security.provider.JavaKeyStore.engineLoad(JavaKeyStore.java:628)
	at sun.security.provider.JavaKeyStore$JKS.engineLoad(JavaKeyStore.java:38)
	at java.security.KeyStore.load(KeyStore.java:1185)
	at com.sun.deploy.security.DeploySigningCertStore$1.run(DeploySigningCertStore.java:154)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.sun.deploy.security.DeploySigningCertStore.loadCertStore(DeploySigningCertStore.java:137)
	at com.sun.deploy.security.DeploySigningCertStore.load(DeploySigningCertStore.java:107)
	at com.sun.deploy.security.DeploySigningCertStore.load(DeploySigningCertStore.java:92)
	at com.sun.deploy.security.ImmutableCertStore.load(ImmutableCertStore.java:43)
	at com.sun.deploy.security.TrustDecider.isAllPermissionGranted(TrustDecider.java:199)
	at com.sun.deploy.security.TrustDecider.isAllPermissionGranted(TrustDecider.java:172)
	at sun.plugin.security.PluginClassLoader.getPermissions(PluginClassLoader.java:145)
	at java.security.SecureClassLoader.getProtectionDomain(SecureClassLoader.java:192)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:155)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:632)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)

Not urgent. Cheers

John

---

### Post by ashwyn on 2008-10-29
I get the exact same error.  Glad to discover that I'm not alone.  I'm running the latest version of Ubuntu eee on an eeepc 701.

The annoying thing is that I have no problems uploading photos from another laptop I have that is also running the latest version of Ubuntu, with the same java plugins.

I have tried uninstalling ad reinstalling everything with the word java in it's description to no avail.

I've also noticed that I get the same error message when I open the 'sun java 6 plugin control panel' from the preferences window, and go to the 'security' tab then click on 'certificates'.

Any idea of what is causing this would be great.  Let me know if I should provide some more information.

---

### Post by John RG on 2008-10-31
Ashwyn, thanks. I checked and got the same error with the Java Control Panel, so we share the same issue. I'll dig around on that error and see what I can find. Cheers, John

---

### Post by vgrisham on 2008-10-31
I'm running Intrepid 64. I get the message "No valid license key for current dns/ip address specified. If you see this message contact site administrator." 

I can use facebook's simple uploader, but dammit, I don't want to. :-({|=

---

### Post by John RG on 2008-11-05
Tried a complete re-load of Ubuntu 8.04 and no joy. Still get "publisher cannot be verified by trusted source error". I suspect this may be a java bug because Ubuntu doesn't have the latest version of Java 6 (according to the Java website), but I'm not expert enough to jump through the hoops to get the latest version. John

---

### Post by vgrisham on 2008-12-07
As a workaround...

Fspot now has an upload interface extension for Facebook. It must be enabled though by going to preferences and Manage Extensions. From there, you can enable the Facebook extension.

---

### Post by John RG on 2008-12-07
The Fspot thing works, thanks. Cheers, John

---

### Post by vgrisham on 2008-12-23
This problem is now resolved for AMD 64 users by installing the new Java for AMD 64 as described in [this]("http://ubuntuforums.org/showthread.php?t=1013658") thread.

---

### Post by Accidus on 2009-01-04
Problem persists in Interpid 32 on a Dell Inspiron 1545.

---

### Post by mongrel boy on 2009-01-16
This is exactly my problem ("No valid license key for current dns/ip address specified. If you see this message contact site administrator."  ) and I don't want to use the simple uploader either!

---

### Post by Morty007 on 2009-03-02
Same issue here. Specs in signature.

---

### Post by thinman1189 on 2009-08-08
Getting this on 8.10 64bit. The fspot plugin works fine though, so I'll just be using that instead. Thanks for the info!

---

