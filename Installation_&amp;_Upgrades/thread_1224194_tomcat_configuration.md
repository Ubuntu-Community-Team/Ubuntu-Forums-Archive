---
title: "tomcat configuration"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by nael on 2009-07-27
hello,
I have installed tomcat6.0.20 on my ubuntu 9.04 using the tutorial in this website:
[http://ubuntuforums.org/showthread.php?p=226828](http://ubuntuforums.org/showthread.php?p=226828)
at the last step after running the command: 
sh /usr/local/tomcat-6.0.20/bin/startup.sh 
as a result I get this:

Using CATALINA_BASE:   /usr/local/tomcat-6.0.20
Using CATALINA_HOME:   /usr/local/tomcat-6.0.20
Using CATALINA_TMPDIR: /usr/local/tomcat-6.0.20/temp
Using JRE_HOME:       /usr/local/jdk1.6.0_14
touch: ne peut faire un touch sur `/usr/local/tomcat-6.0.20/logs/catalina.out': Permission non accordée
./catalina.sh: 375: cannot create /usr/local/tomcat-6.0.20/logs/catalina.out: Permission denied

instead of this:

Using CATALINA_BASE:   /usr/local/tomcat-6.0.20
 Using CATALINA_HOME:   /usr/local/tomcat-6.0.20
 Using CATALINA_TMPDIR: /usr/local/tomcat-6.0.20/temp
 Using JRE_HOME:       /usr/local/jdk1.6.0_14

which means that a problem occured!!!!!

how can I fix this problem???

thankyou for the help

---

### Post by davetv on 2009-07-27
It's probably a permissions issue on the /usr/local/tomcat-6.0.20/logs/ folder.

Try the command "sudo chmod 777 /usr/local/tomcat-6.0.20/logs"

---

### Post by Blond1n on 2010-10-29
[LEFT]Thanks Davetv for letting me know about the "sudo chmod 777" syntax, 'saved for antoher permission problem ! :)
[/LEFT]

---

