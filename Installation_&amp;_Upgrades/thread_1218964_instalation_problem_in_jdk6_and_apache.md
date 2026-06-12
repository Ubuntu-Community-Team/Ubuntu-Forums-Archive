---
title: "instalation problem in jdk6 and apache"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by faizan_comsian on 2009-07-21
HI
i got following information from the same forum....to install jdk before tomcat


sudo apt-get install sun-java6-jdk

after that to check is it working properly

dpkg –get-selections | grep sun-java

it must show this output:

    sun-java6-bin                                   install
    sun-java6-jdk                                   install
    sun-java6-jre                                   install

BUT MY PROBLEM IS:

he is showing this output :

dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
PLEASE HELP ME OUT

More Information:
I am new in ubuntu field i dont know what that output means,and i had already installed jdk6 from add/remove. and then i installed it again according to above info

---

### Post by Partyboi2 on 2009-07-21
Hi, add a extra " - " to the command so
```
dpkg **[COLOR=Red]--[/COLOR]**get-selections | grep sun-java
```

---

### Post by faizan_comsian on 2009-07-21
thnx alote for "-". forther i'll check

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

### Post by faizan_comsian on 2009-08-10
i got the solutions.text to be pasted at the end of that file...and permission denied is just because i were not SU  in root

---

