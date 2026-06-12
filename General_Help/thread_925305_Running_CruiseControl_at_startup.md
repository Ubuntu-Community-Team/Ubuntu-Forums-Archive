---
title: "Running CruiseControl at startup"
date: 2008-09-20
forum: General Help
---

### Post by miggl on 2008-09-20
Hi folks!

I have managed to get CruiseControl ([http://cruisecontrol.sourceforge.net/](http://cruisecontrol.sourceforge.net/)) installed, well... somewhat.
There are a few quandaries I am trying to overcome:

[LIST=1]
[*]How to get CruiseControl to work from /opt/cruisecontrol/ directory, instead of ~/cruisecontrol/.
[*]How to get CruiseControl to run at startup.
[/LIST]

I guess the main problem is #1: When installing it per these instructions ([http://no-names.biz/2008/06/09/cruisecontrol-and-phpundercontrol-in-debian-etch/](http://no-names.biz/2008/06/09/cruisecontrol-and-phpundercontrol-in-debian-etch/)) I receive the following error when trying to start cruisecontrol:
> mike@sol:/opt/cruisecontrol$ sudo ./cruisecontrol.sh
Using Cruise Control at /opt/cruisecontrol-bin-2.7.3
/bin/java -Djavax.management.builder.initial=mx4j.server.MX4JMBeanServerBuilder -Dcc.library.dir=/opt/cruisecontrol-bin-2.7.3/lib -jar /opt/cruisecontrol-bin-2.7.3/lib/cruisecontrol-launcher.jar -jmxport 8000 -webport 8080 -rmiport 1099
./cruisecontrol.sh: line 102: /bin/java: No such file or directory


Note: I'm using SUDO here because it would use the same permissions if trying to start it from /etc/rc.local (which doesn't work).

I've narrowed the error down to the JAVA_HOME environment variable not being read correctly, even though:
> mike@sol:/opt/cruisecontrol$ sudo echo $JAVA_HOME
/usr/lib/jvm/java-6-sun


Does anyone have any advice?

Thanks!

---

### Post by hexusff on 2008-10-01
Hi i crush with the same problem, apparently cruise control has hardcoded that path, so I made a symbolic link to the java binary
```
$ ln -s /usr/lib/jvm/java-6-sun/bin/java /bin/java
```
This solved this problem, maybe some one got a better way to get this tool running

---

### Post by RussellEngland on 2011-08-18
Brilliant, thank you :)

---

