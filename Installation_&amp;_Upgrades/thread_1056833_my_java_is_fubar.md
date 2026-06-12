---
title: "my java is fubar"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2009-02-01
I'm trying to get a java program running by switching to sun java, but it seems to have mysteriously gone haywire. I've tried to remove and install java-6-sun through apt, but i still get error messages:


```
**khaal@Xeraphim:~/$ sudo update-java-alternatives -l**
sudo: cannot get working directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
java-6-cacao 1059 /usr/lib/jvm/java-6-cacao
java-6-sun 63 /usr/lib/jvm/java-6-sun

```

```
**khaal@Xeraphim:~/$ sudo update-java-alternatives -s java-6-sun**
sudo: cannot get working directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for appletviewer.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for apt.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for extcheck.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for firefox-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for HtmlConverter.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for iceape-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for iceweasel-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for idlj.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jar.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jarsigner.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for javac.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for javadoc.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for javah.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for javap.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for java-rmi.cgi.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jconsole.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jdb.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jhat.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jinfo.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jmap.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jps.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jrunscript.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jsadebugd.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jstack.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jstat.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for jstatd.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for midbrowser-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for mozilla-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for native2ascii.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for pluginappletviewer.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for rmic.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for schemagen.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for serialver.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for wsgen.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for wsimport.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for xjc.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for xulrunner-1.9-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for xulrunner-javaplugin.so.
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
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for firefox-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for iceape-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for iceweasel-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for midbrowser-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for mozilla-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for xulrunner-1.9-javaplugin.so.
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
No alternatives for xulrunner-javaplugin.so.

```


help would be most appriciated!

---

### Post by x33a on 2009-02-01
well, best bet would be to purge remove if anything's left, and search and delete all configuration files manually.

---

### Post by KhaaL on 2009-02-01
that did it, thanks :)

---

