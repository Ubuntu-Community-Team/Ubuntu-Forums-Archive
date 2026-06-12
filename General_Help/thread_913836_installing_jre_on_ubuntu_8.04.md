---
title: "installing jre on ubuntu 8.04"
date: 2008-09-08
forum: General Help
---

### Post by lookforlohith on 2008-09-08
sir i tried to install jre ... applet support

i tried and im getting error..... please help

i tried "lohi@look:~$ sudo apt-get install sun-java6-jre"


lohi@look:~$ sudo apt-get install sun-java6-jre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 252 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tomcat5.5 (5.5.25-5ubuntu1) ...
 * Starting Tomcat servlet engine tomcat5.5                                                                                 cat: /etc/tomcat5.5/policy.d/05solr.policy: No such file or directory
invoke-rc.d: initscript tomcat5.5, action "start" failed.
dpkg: error processing tomcat5.5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of solr-tomcat5.5:
 solr-tomcat5.5 depends on tomcat5.5 (>= 5.5.20); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing solr-tomcat5.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tomcat5.5-admin:
 tomcat5.5-admin depends on tomcat5.5 (>= 5.5.25-5ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-admin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tomcat5.5
 solr-tomcat5.5
 tomcat5.5-admin
E: Sub-process /usr/bin/dpkg returned an error code (1)



my version java

lohi@look:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)


"im unable to open applets "................ please help

---

### Post by jonface on 2008-09-08
In ~/.mozilla/plugins/ , do you have a file called 'libjavaplugin_oji.so' ? Mine is a symbollic link to, 

/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so 

The thing is, you're using the OpenJDK so I don't know if it all works the same I'm afraid. See if you can find libjavaplugin_oji.so first.

---

### Post by boldexplorer on 2008-09-08
Hi there. 
When I first setup my Ubuntu I was having similar problems. I decided to sod it, I was not going back to Windows. So I had a big problem. The solution was simple enough.
I downloaded the Sun Java package from their website ([http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)) and followed the instructions.
Two notes on the instructions: First be very uber careful when becoming su! 
it is far better to sudo. 
Second: once downloaded move the file to somewhere like /usr/java make the directory if necessary (mkdir java).
This seems to work fine for my applications.

Have Fun!

---

### Post by zvacet on 2008-09-08
```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

Why don´t you install Java from synaptic,or maybe with 

```
sudo apt-get install ubuntu-restricted-extras
```

You will get Java and other things I think you will need anyway.

---

