---
title: "Does tomcat6 work in 8.10 Intrepid Ibex?"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by ScottCh on 2008-12-16
Hi Folks,

I have tomcat6 installed and it appears to be running.  But when I open firefox and enter [http://localhost:8080](http://localhost:8080), it reports "failed to connect".

In addition, "netstat -ant" shows no connections for any four digit port number starting with 8.  As far as I can tell, tomcat was not able to open a port connection for its service.

The reason I think it is running is that my process list shows tomcat processes.  If I stop tomcat (e.g. "service tomcat6 stop") they go away.  If I start it, they come back.  

Here's what the process listing looks like:

[INDENT]root      9933  0.0  0.0   2136   360 ?        Ss   10:10   0:00 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile /var/run/tomcat6.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/var/lib/tomcat6/temp -Djava.security.manager -Djava.security.policy=/var/lib/tomcat6/work/catalina.policy -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties org.apache.catalina.startup.Bootstrap[/INDENT]

In addition, the tomcat log file (in /var/log/tomcat6) says it has started running:

[INDENT]Dec 16, 2008 10:03:25 AM org.apache.catalina.core.AprLifecycleListener init
INFO: APR capabilities: IPv6 [true], sendfile [true], accept filters [false], random [true].[/INDENT]

What I suspected at first was that tomcat is not able to create its ports because of firewall restrictions.  But I have stopped the firewall using "sudo service ufw stop", and then restarted tomcat6.  This made no difference.

I have installed tomcat6 many times on CentOS and Windows platforms, where it runs fine.  However, I'm still figuring out how tomcat is configured when installed from the debian packages.  Maybe I've missed an important detail?

I used "sudo apt-get install tomcat6 tomcat6-admin tomcat6-docs tomcat6-examples" to install tomcat6 on my ubuntu intrepid installation.  

Has anyone gotten tomcat6 to run successfully on this distro?  Any insights?  Thanks for any help.

Scott C. in Cary, NC USA

---

### Post by jamesstansell on 2008-12-16
Some general-purpose tools that are handy to be familiar with are fuser and lsof.  I guess lsof would be more useful in this case.

Also, you could try netstat -pltn and look for your tomcat pid.

HTH,

-james.

P.S. If you have the visualvm program installed (called jvisualvm in a JDK install) it may show some interesting information.

---

