---
title: "Upgrade to Tomcat 6 causes a LogConfigurationException"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2009-04-05
Hi,

I have a couple of webapps that worked fine on Centos 4.6 and Tomcat 5.5.26. I have just upgraded to Ubuntu 8.10 Server amd64 with Tomcat 6 and they no longer run. After some googling could not find a definative answer on how to rectify.

Here is the exception from the Catalina log file:
org.apache.commons.logging.LogConfigurationException: User-defined log class 'org.apache.commons.logging.impl.Log4JLogger' cannot be found or is not usable.

The webapsp still have both log4j-1.2.8.jar and commons-logging-1.0.4.jar in their WEB-INF/lib directories and also have commons-logging.properties and log4j.properties in the WEB-INF/classes directory. I tried updating to commons-logging-1.1.1.jar making no difference. 

Since Tomcat6 no longer uses commons logging the old classloader issue should no longer be there, as was with Tomcat 5.5. ( Which was easily solved by moving the jar to /server/lib ).

Any ideas on how to fix this?

Thx.

David

---

