---
title: "Java help"
date: 2008-09-14
forum: General Help
---

### Post by gaviota on 2008-09-14
I thought I had Java installed and working in my pc, but it doesn't work when I open a web page that requires Java. I open this same page using another PC with Vista and Microsoft Internet Explorer and it works.

I initially see the Java logo in the Mozilla Firefox window, but then I get the X that means its not working. When I open the Java console I get the following error:

cargar: clase jplug.class no encontrada.
java.lang.ClassNotFoundException: jplug.class
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:194)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:640)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)

I have Ubuntu 8.04 Hardy Heron in Spanish, so that's why I get the error message in Spanish.

How can I solve this problem?

Thanks in advance.

---

### Post by gaviota on 2008-09-15
Anyone, please???

---

### Post by scouser73 on 2008-09-16
If you can, try uninstalling the ghost Java, then reinstall it, it's worth a try I guess

---

### Post by jespdj on 2008-09-16
Java can't find a class (jplug.class) that it's supposed to run. This is most likely an error by the person who made the website.

Which website is it? Does it work on other systems or do you get the same error?

---

### Post by gaviota on 2008-09-17
More details in the problem, which still persists...

I tried reinstalling with the following:

sudo apt-get sun-java6-jre

It ran without any errors.


Now, if I run:

java -version

I get the following:

java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)

So Java is supposed to be installed correctly.


But if I open the webpage of my home surveilance camera (TrendNet TV-IP400), I get the attached screenshot. I only get the Java icon, but no camera image. This same webpage works perfectly in my other PC with Microsoft Vista and Microsoft Internet Explorer.

I also try with my bank's webpage, and it doesn't work with my Ububtu/Firefox PC either, but works fine with my Microsoft Vista/Internet Explorer PC.

When I open the Java console I get the following:

cargar: clase jplug.class no encontrada.
java.lang.ClassNotFoundException: jplug.class
at sun.applet.AppletClassLoader.findClass(AppletClass Loader.java:194)
at java.lang.ClassLoader.loadClass(ClassLoader.java:3 06)
at sun.applet.AppletClassLoader.loadClass(AppletClass Loader.java:127)
at java.lang.ClassLoader.loadClass(ClassLoader.java:2 51)
at sun.applet.AppletClassLoader.loadCode(AppletClassL oader.java:640)
at sun.applet.AppletPanel.createApplet(AppletPanel.ja va:786)
at sun.plugin.AppletViewer.createApplet(AppletViewer. java:210
at sun.applet.AppletPanel.runLoader(AppletPanel.java: 715)
at sun.applet.AppletPanel.run(AppletPanel.java:369)
at java.lang.Thread.run(Thread.java:619)

I have Ubuntu 8.04 Hardy Heron in Spanish, so that's why I get the error message in Spanish.

Any other suggestions, please???

---

### Post by gaviota on 2008-09-22
Anyone, please?

---

### Post by ju2wheels on 2008-09-22
Your system java is still set to OpenJdk, you need to make Sun Java 6 the default.

Do the following:
```

sudo update-java-alternatives -s java-6-sun

```

Then make sure that the first line in /etc/jvm shows sun java 6 first like this:

```

sudo gedit /etc/jvm

```

Contents:
```

# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

```

Edit:
--------
Also you should be installing these packages:
```

sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by gaviota on 2008-09-22
Thanks for your answer. I followed your instructions. Output for the first step is:

root@jcisne-desktop:/home/jcisne# sudo update-java-alternatives -s java-6-sun
No hay alternativas para appletviewer.
No hay alternativas para apt.
No hay alternativas para extcheck.
No hay alternativas para HtmlConverter.
No hay alternativas para idlj.
No hay alternativas para jar.
No hay alternativas para jarsigner.
No hay alternativas para javac.
No hay alternativas para javadoc.
No hay alternativas para javah.
No hay alternativas para javap.
No hay alternativas para java-rmi.cgi.
No hay alternativas para jconsole.
No hay alternativas para jdb.
No hay alternativas para jhat.
No hay alternativas para jinfo.
No hay alternativas para jmap.
No hay alternativas para jps.
No hay alternativas para jrunscript.
No hay alternativas para jsadebugd.
No hay alternativas para jstack.
No hay alternativas para jstat.
No hay alternativas para jstatd.
No hay alternativas para native2ascii.
No hay alternativas para rmic.
No hay alternativas para schemagen.
No hay alternativas para wsgen.
No hay alternativas para wsimport.
No hay alternativas para xjc.
No hay alternativas para xulrunner-addons-javaplugin.so.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' para proporcionar `ControlPanel'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/java' para proporcionar `java'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/java_vm' para proporcionar `java_vm'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/javaws' para proporcionar `javaws'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' para proporcionar `jcontrol'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/keytool' para proporcionar `keytool'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/orbd' para proporcionar `orbd'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/pack200' para proporcionar `pack200'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/policytool' para proporcionar `policytool'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/rmid' para proporcionar `rmid'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' para proporcionar `rmiregistry'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/servertool' para proporcionar `servertool'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' para proporcionar `tnameserv'.
Se utiliza `/usr/lib/jvm/java-6-sun/jre/bin/unpack200' para proporcionar `unpack200'.
No hay alternativas para xulrunner-addons-javaplugin.so.



For the second step I edited the /etc/jvm file exactly like you stated, no problems there.


For the third step I got the following output:

root@jcisne-desktop:/home/jcisne# sudo apt-get install sun-java6-jre sun-java6-plugin
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
sun-java6-jre ya está en su versión más reciente.
sun-java6-plugin ya está en su versión más reciente.
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  gappletviewer-4.2
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.


Then I restarted my browser, but I still get the following error on my Java console:

cargar: clase jplug.class no encontrada.
java.lang.ClassNotFoundException: jplug.class
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:194)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:640)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)

What can be wrong?

---

### Post by ju2wheels on 2008-09-22
Sorry I put the commands out of order.

It had to be done in this order:
```

sudo apt-get install sun-java6-jre sun-java6-plugin
sudo update-java-alternatives -s java-6-sun

```

Since you already installed the packages just run the second line again. Also be sure to close all browsers and reload them again.

If it doesnt work after this then it is a problem with the java program on the website.

Edit
--------
From your output it looks like you already had sun-java6-plugin installed, it might be a problem with the website and the way the java code was written and packaged...

---

### Post by gaviota on 2008-09-22
Thanks again, but I still get the same error :(

I tried it with 2 separate webpages, neither worked. Then I tried them both with my Microsoft Vista/Internet Explorer PC and they both work :(

Is there another plugin I need to install?

---

### Post by ju2wheels on 2008-09-22
No, that should be it. Are you running 32bit Ubuntu or 64bit? Thats the only other thing I can think of that will cause you problems.

---

### Post by gaviota on 2008-09-23
I'm running 32 bit.

---

