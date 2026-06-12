---
title: "Java Runtime Environment (JRE)"
date: 2008-11-02
forum: General Help
---

### Post by huwaw69 on 2008-11-02
i have updated my java form [http://www.java.com](http://www.java.com) to the latest jre version and java version...
The latest java version is 1.6.something but in terminal i type:
java --version
it says my java version is 1.5.something...
i checked my version at [http://www.java.com](http://www.java.com)
the website says my java is 1.6.something so it means it's the latest..
whats seems to be the problem here? all the solution i have in mind is useless... 

I really nid it for frostwire so i can download songs and i nid for some further necessities...

---

### Post by naugiedoggie on 2008-11-02
> **huwaw69 said:**
> i have updated my java form [http://www.java.com](http://www.java.com) to the latest jre version and java version...
The latest java version is 1.6.something but in terminal i type:
java --version
it says my java version is 1.5.something...
i checked my version at [http://www.java.com](http://www.java.com)
the website says my java is 1.6.something so it means it's the latest..
whats seems to be the problem here? all the solution i have in mind is useless... 

I really nid it for frostwire so i can download songs and i nid for some further necessities...

Hello,

Because if you just install something manually, the version installed by the package manager is probably the one that all your software points to.  You have to fix things manually when you don't use the package manager.  For example, 

```
powem@cecilia:~$ which java
/usr/bin/java
powem@cecilia:~$ ls -al /usr/bin/java
lrwxrwxrwx 1 root root 22 2008-01-13 07:32 /usr/bin/java -> /etc/alternatives/java
powem@cecilia:~$ ll /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2008-05-13 13:36 /etc/alternatives/java -> /usr/lib/jvm/java-6-sun/jre/bin/java
powem@cecilia:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

That is the default installation.  When you install your new version, at the minimum you will have to either (a) replace the link /usr/bin/java to point to the new version or (b) put the bin directory of the new version ahead of the default location in your PATH variable, so that the system sees it first.

The first option is probably preferable.

Thanks.

mp

Oh yeah:  I believe by default Ubuntu installs one of the Java knockoffs, rather than the orignal from Sun.  So, even though it says "Java" it's Blackdown or Kaffe or something similar.  I forgot that I replaced that with the Sun version.

---

### Post by reality1011 on 2008-11-02
type : which java on the command line... 

Then type: ls -al on the path that the above gave you  (probably /usr/bin/java)

I bet its still pointing to the 1.5 libaries...

if this is the case you need to delete the /usr/bin/java link and relink it to the new java 

to create a link be in /usr/bin/ directory and do the following: ln [COLOR="Red"]<path_of_new_java_install_bin_folder>[/COLOR]/java java

I placed /java in there to explicitly point to the java binary and the second java is there to be placed into the /usr/bin/ directory, which replaces the one you deleted.  

You should also do this for any other binaries but definitely javac

---

### Post by reality1011 on 2008-11-02
sorry duplicate post

---

### Post by huwaw69 on 2008-11-02
Definetly Good i think i can solve my problem w/ your solutions "IF" im not new in this terminal thing so could you slow down a bit?

---

