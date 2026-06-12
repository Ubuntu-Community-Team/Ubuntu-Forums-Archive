---
title: "run tomcat 5.5 as a daemon"
date: 2008-08-12
forum: General Help
---

### Post by asaf.lahav on 2008-08-12
Hi everybody,
I'm currently able to initialize tomcat properly from command line.
Yet, having trouble configuring it property to run as daemon.
How to configure tomcat 5.5 to run as a daemon?
Thanks in advance,
Asaf

---

### Post by hal8000 on 2008-08-12
See if this post helps:

[http://ubuntuforums.org/showthread.php?t=44006](http://ubuntuforums.org/showthread.php?t=44006)

---

### Post by asaf.lahav on 2008-08-12
> **hal8000 said:**
> See if this post helps:

[http://ubuntuforums.org/showthread.php?t=44006](http://ubuntuforums.org/showthread.php?t=44006)

I followed the enclosed article. And when I am running the following command (which is not as a daemon. i just wanted to make sure it works before restarting):
```
sh /etc/init.d/tomcat start
```

I get the following output:
$ sh /etc/init.d/tomcat start
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.15
touch: cannot touch `/usr/local/tomcat/logs/catalina.out': Permission denied
/usr/local/tomcat/bin/catalina.sh: 340: cannot create /usr/local/tomcat/logs/catalina.out: Permission denied

What security settings are required for it run properly?

---

### Post by asaf.lahav on 2008-08-12
OK... I modified the permissions and now tomcat runns perfectly when I initiate it from command line.
But I'm still unable to get it to run as a daemon.

Here is the script I put in the init.d dir:
#!/bin/bash
#
# Startup script for the Tomcat server
#
# chkconfig: - 83 53
# description: Starts and stops the Tomcat daemon.
# processname: tomcat
# pidfile: /var/run/tomcat.pid


# See how we were called.
case $1 in
	start)

		export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.15
		export CLASSPATH=/usr/local/tomcat/common/lib/servlet-api.jar
		export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar
		sh /usr/local/tomcat/bin/startup.sh
	;;
	stop)
		sh /usr/local/tomcat/bin/shutdown.sh
	;;
	restart)
		sh /usr/local/tomcat/bin/shutdown.sh
		sh /usr/local/tomcat/bin/startup.sh
	;;
	*)
		echo "Usage: /etc/init.d/tomcat start|stop|restart"
	;;
esac

exit 0

Why doesn't it fire properly?

---

### Post by futureOS on 2008-08-12
anyone please tell me how to install it...
i found it really hard to install...i need it so can install [openlaszlo]("http://openlaszlo.org")
thanks guys !!!

---

### Post by asaf.lahav on 2008-08-12
Is there a log where I can see whether the System tried to initialize the tomcat shell script?

---

### Post by datajelly on 2008-08-26
It looks as if you don't have permissions to write to /usr/local/tomcat/logs/catalina.out. What happens if you run the startup script as root?
```
sudo /etc/init.d/tomcat start
```

For reference, I have installed Tomcat 6 if you wanted to check out my [startup script]("http://blog.datajelly.com/2008/08/installing-apache-tomcat-6-on-ubuntu.html"). I'm not too sure how similar Tomcat5.5 and Tomcat6 would be.

---

