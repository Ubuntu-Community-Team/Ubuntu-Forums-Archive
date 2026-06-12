---
title: "newbie: java, environment variables, eclipse"
date: 2008-11-09
forum: General Help
---

### Post by dworq on 2008-11-09
His, Community, 

Finally decided to switch to Ubuntu. I am a starting java developer working under Windows and Eclipse. A bit confused about the setup steps and their diversity need to be done under linux, if anyone could suggest the best practices: 

I suspect that the questions are most likely excessive and have been raised and explained a number of times before. Maybe there is a recommended tutorial that every aspiring developer should read. I am just confused by obundance of the materials and do not know which ones I should follow. 

* I see that java leads to "/usr/bin/java" -> "/etc/alterm/java-6-openjdk/jre/bin/java". That means that I have OpenJDK as java as opposed to Java from SUN. What is the difference though? How could I install java from Sun and safely delete the OpenJDK so that no current applications stop working? Yeah, and I see 
"/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun"
when running "vi /etc/jvm". No OpenJDK reference? What does that mean?

* How do I set environment variables. Is is done per user or globally for every user? Is it .profile or .bashrs that need to be changed? 

* Where the Eclipse be installed. I mean there are so many opt, usr, home? I am not getting what are the considerations behind choosing the installation folder. 

Greately appreciate every hint and suggestion. 
Thanks

---

### Post by Nepherte on 2008-11-09
If you're on a 64bit, I suggest you keep the openjdk one as it's the only one that has a 64bit java browser plugin. Otherwise it's a matter of preference. You can install the official sun java with:
```
sudo apt-get install sun-java6-jre
```
Replace jre with jdk if you need the other one.

and you can remove openjdk with:
```
sudo apt-get remove openjdk-6-jre
```
You can keep openjdk if you like, but if you keep it, you might want to set sun java as default:
```
sudo update-alternatives --config java
```
and choose the correct one.

Now when you're using sun java, /etc/jvm is ok. If you want to keep openjdk, add the path to openjdk as the first entry in /etc/jvm.

---

### Post by jespdj on 2008-11-09
[OpenJDK](http://openjdk.java.net/) is Sun's project to make Java open source. It works just as well as Sun Java, unless you have a specific problem there is no need to worry that it isn't compatible, so there's no need to uninstall it. Eclipse runs fine on OpenJDK Java. But if you really want Sun Java 6, do this:
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
sudo update-alternatives --config java
```
The second command lets you choose which Java you want to use by default.

You can set environment variables by editing .profile (in your home directory), for example. Those settings are per user.

If you installed Eclipse from the Ubuntu software repository, you can use this command to see which files were installed for Eclipse:
```
dpkg -L eclipse
```

---

### Post by dworq on 2008-11-09
Thanks! 

Is there a place which describes these steps. I mean, I see so many ways of doing things but do not know what the best practices are. 

For instance, I am setting user environment variables in .profile not in .bashrc ([http://www.laliluna.de/blog/2007/02/22/ubuntu_environment_variable_java_home.html]("http://www.laliluna.de/blog/2007/02/22/ubuntu_environment_variable_java_home.html"))? 

So I basically can have both OpenJDK and Java installed parallel to each other and specify than only one of them should be used. What happens under the hood after calling "sudo update-alternatives --config java"? What if I do not use package manager but download java direct from the website? 

Thanks

---

