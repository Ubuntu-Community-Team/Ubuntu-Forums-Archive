---
title: "facing problem to configure apache plz help me out"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by faizan_comsian on 2009-07-22
NOW I have a problem to configure apache PLZ HELP ME OUT:
After downloading apache i did this "tar xvzf apache-tomcat-6.0.14.tar.gz" to this file "apache-tomcat-6.0.14.tar.gz" but i got error :
tar: apache-tomcat-6.0.14.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

BUT I AVOID THIS AT THAT POINT OF TIME AND DID SUCCESSFULLY:
sudo mv apache-tomcat-6.0.14 /usr/local/tomcat  

THEN I NEED TO DO THIS STEP BUT:
gedit ~/.bashrc
Add the following line:
export JAVA_HOME=/usr/lib/jvm/java-6-sun
(I DON'T KNOW AT WHICH PLACE OF THAT FILE I ADD IT)

More Info:
He is not giving me the permission to execute startup.sh of tomcat and i haven't found /etc/init.d/tomcat as well to make it auto start at login point of time by adding this line sudo gedit /etc/init.d/tomcat

---

### Post by faizan_comsian on 2009-08-01
i got it....it should be at the end

---

