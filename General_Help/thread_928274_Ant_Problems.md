---
title: "Ant Problems"
date: 2008-09-23
forum: General Help
---

### Post by scott_s on 2008-09-23
I've been trying to compile a database server (MonetDB) from source, and the compilation of the JDBC driver has been failing with the message "Bad version number in .class file"  People on the MonetDB listserv suggested that this was likely a java version mismatch, and also suggested that I look into my ant settings to see if it was using the wrong version of java (ant is used to build the JDBC driver).  I ran ant -diagnostics and look what popped out:

```

 ant -diagnostics
------- Ant diagnostics report -------
Apache Ant version 1.7.0 compiled on September 8 2008

-------------------------------------------
 Implementation Version
-------------------------------------------
core tasks     : 1.7.0
optional tasks : not available

-------------------------------------------
 ANT PROPERTIES
-------------------------------------------
ant.version: Apache Ant version 1.7.0 compiled on September 8 2008
ant.java.version: 1.5
ant.core.lib: /usr/share/ant/lib/ant.jar
ant.home: /usr/share/ant

-------------------------------------------
 ANT_HOME/lib jar listing
-------------------------------------------
ant.home: /usr/share/ant
junit.jar (73358 bytes)
catalina5.5-ant-jmx.jar (25221 bytes)
ant-nodeps.jar (428623 bytes)
ant-apache-bcel.jar (8594 bytes)
ant-junit.jar (92539 bytes)
bcel.jar (528635 bytes)
ant-commons-logging.jar (3909 bytes)
ant-apache-log4j.jar (3059 bytes)
ant-apache-bsf.jar (3968 bytes)
jsch.jar (210087 bytes)
ant-launcher.jar (11716 bytes)
ant-jmf.jar (6594 bytes)
tomcat5.5-jkstatus-ant.jar (32415 bytes)
ant-apache-resolver.jar (4069 bytes)
ant-jsch.jar (29980 bytes)
catalina5.5-ant.jar (27954 bytes)
ant-antlr.jar (5746 bytes)
ant-apache-regexp.jar (3728 bytes)
ant-jdepend.jar (8136 bytes)
ant-commons-net.jar (46882 bytes)
ant.jar (1309307 bytes)
ant-trax.jar (6881 bytes)
ant-apache-oro.jar (39524 bytes)
ant-javamail.jar (6998 bytes)
ant-swing.jar (6674 bytes)

-------------------------------------------
 USER_HOME/.ant/lib jar listing
-------------------------------------------
user.home: /home/scott
No such directory.

-------------------------------------------
 Tasks availability
-------------------------------------------
image : Not Available (the implementation class is not present)
sshexec : Initialization error
wlrun : Not Available (the implementation class is not present)
scp : Initialization error
stlist : Not Available (the implementation class is not present)
netrexxc : Not Available (the implementation class is not present)
starteam : Not Available (the implementation class is not present)
stylebook : Not Available (the implementation class is not present)
stlabel : Not Available (the implementation class is not present)
jdepend : Missing dependency jdepend.xmlui.JDepend
stcheckin : Not Available (the implementation class is not present)
stcheckout : Not Available (the implementation class is not present)
ejbc : Not Available (the implementation class is not present)
wlstop : Not Available (the implementation class is not present)
ddcreator : Not Available (the implementation class is not present)
A task being missing/unavailable should only matter if you are trying to use it

-------------------------------------------
 org.apache.env.Which diagnostics
-------------------------------------------
Not available.
Download it at http://xml.apache.org/commons/

-------------------------------------------
 XML Parser information
-------------------------------------------
Bad version number in .class file

```

The last line makes me think there is something wrong with my ant installation, which in turn may be something wrong with the Ubuntu packages, since I just installed the ant package.  Anybody have any thoughts as to what might be going on?  I'm running the Intrepid Ibex alpha, AMD64 version.

---

### Post by dcraven on 2008-09-23
Try running 'ant clean' or 'ant clobber' or whatever target like that is available. I've seen that when some class files have been built with one version of java, and the rest with another.

Cleaning up the build and trying again will remove the already built class files and rebuild with the current javac version.

I don't know anything about the project you are trying to build, but this might help.

~djc

---

### Post by scott_s on 2008-09-23
The error above happens even without trying to build something but simply when running the ```
ant -diagnostics
``` command.  Nonetheless, I ran ant clean on the build.xml file and got the following error:

```

ant clean
Buildfile: build.xml

BUILD FAILED
java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:299)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at javax.xml.parsers.FactoryFinder.newInstance(FactoryFinder.java:88)
	at javax.xml.parsers.FactoryFinder.findJarServiceProvider(FactoryFinder.java:278)
	at javax.xml.parsers.FactoryFinder.find(FactoryFinder.java:185)
	at javax.xml.parsers.SAXParserFactory.newInstance(SAXParserFactory.java:107)
	at org.apache.tools.ant.util.JAXPUtils.newParserFactory(JAXPUtils.java:120)
	at org.apache.tools.ant.util.JAXPUtils.getNSParserFactory(JAXPUtils.java:104)
	at org.apache.tools.ant.util.JAXPUtils.getNamespaceXMLReader(JAXPUtils.java:172)
	at org.apache.tools.ant.helper.ProjectHelper2.parse(ProjectHelper2.java:185)
	at org.apache.tools.ant.helper.ProjectHelper2.parse(ProjectHelper2.java:138)
	at org.apache.tools.ant.ProjectHelper.configureProject(ProjectHelper.java:96)
	at org.apache.tools.ant.Main.runBuild(Main.java:683)
	at org.apache.tools.ant.Main.startAnt(Main.java:199)
	at org.apache.tools.ant.launch.Launcher.run(Launcher.java:257)
	at org.apache.tools.ant.launch.Launcher.main(Launcher.java:104)

Total time: 0 seconds
java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:299)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at javax.xml.parsers.FactoryFinder.newInstance(FactoryFinder.java:88)
	at javax.xml.parsers.FactoryFinder.findJarServiceProvider(FactoryFinder.java:278)
	at javax.xml.parsers.FactoryFinder.find(FactoryFinder.java:185)
	at javax.xml.parsers.SAXParserFactory.newInstance(SAXParserFactory.java:107)
	at org.apache.tools.ant.util.JAXPUtils.newParserFactory(JAXPUtils.java:120)
	at org.apache.tools.ant.util.JAXPUtils.getNSParserFactory(JAXPUtils.java:104)
	at org.apache.tools.ant.util.JAXPUtils.getNamespaceXMLReader(JAXPUtils.java:172)
	at org.apache.tools.ant.helper.ProjectHelper2.parse(ProjectHelper2.java:185)
	at org.apache.tools.ant.helper.ProjectHelper2.parse(ProjectHelper2.java:138)
	at org.apache.tools.ant.ProjectHelper.configureProject(ProjectHelper.java:96)
	at org.apache.tools.ant.Main.runBuild(Main.java:683)
	at org.apache.tools.ant.Main.startAnt(Main.java:199)
	at org.apache.tools.ant.launch.Launcher.run(Launcher.java:257)
	at org.apache.tools.ant.launch.Launcher.main(Launcher.java:104)
Bad version number in .class file


```

It seems to me that whatever facility allows ant to parse XML files is broken somehow.

---

### Post by scott_s on 2008-09-23
So installing Sun Java 1.6 and setting it to the default fixes the problem from ```
ant -diagnostics
```... but MonetDB requires Java 1.4 or 1.5.  I guess I'll give it a shot anyway and see how it goes.

---

