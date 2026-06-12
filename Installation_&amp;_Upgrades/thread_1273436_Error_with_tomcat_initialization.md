---
title: "Error with tomcat initialization"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by netgear on 2009-09-23
Hello,

I'm not able to get my .war file deployed in the tomcat webapp. I get the warning like this one - 

p 23, 2009 10:46:43 AM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/local/java/jre/lib/i386/server:/usr/local/java/jre/lib/i386:/usr/local/java/jre/../lib/i386:/usr/local/lib


I tried to install Apache Portable Runtime (APR2.3.8) at [http://mirror.candidhosting.com/pub/apache/apr/](http://mirror.candidhosting.com/pub/apache/apr/) and that does not help either. I did not check which version would be compatible. 

besides my $JAVA_HOME is properly set.

Thanks

---

