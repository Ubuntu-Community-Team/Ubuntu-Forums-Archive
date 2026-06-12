---
title: "OpenOffice.org can't find JRE"
date: 2008-07-17
forum: General Help
---

### Post by wiberg on 2008-07-17
Hi,

I'm having trouble finding the JRE my OpenOffice.org. I'm trying to add the JRE in OpenOffice.org->Options->OpenOffice.org->Java. There are no JREs listed, even though I have one installed (works fine in eclipse). I'm searching for the JRE in /usr/lib/jvm/java-6-sun-1.6.0.06 and all the subdirectories but I always get the message "The folder you selected does not contain a Java Runtime Environment. Please select a different folder".

System:
Ubuntu 8.04 (32bit)
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
OOo 2.4 (came preinstalled with Ubuntu, I never changed anything)

---

### Post by fragos on 2008-07-17
It takes some time for Open Office to find the java jre's, so don't expect it to pop up instantly. It will tell you the location of the selected jave, you can have many. I installed Sun Java 6 with Synaptic and it shows up automatically. It appears that the add button will allow you include java that has been installed in a non standard way. My copies are at:

/usr/lib/jvm/java-6-sun-1.6.0.06/jre
/usr/lib/jvm/java-6-openjdk/jre

---

### Post by jamesstansell on 2008-07-17
> **wiberg said:**
> Hi,

OOo 2.4 (came preinstalled with Ubuntu, I never changed anything)

Make sure you have the openoffice.org-java-common package installed.  I've seen some other people that had java problems because the default install of ubuntu didn't include it.

---

### Post by wiberg on 2008-07-23
Thanks, jamesstansell! That was it. Kinda weird that it isn't installed by default.

---

