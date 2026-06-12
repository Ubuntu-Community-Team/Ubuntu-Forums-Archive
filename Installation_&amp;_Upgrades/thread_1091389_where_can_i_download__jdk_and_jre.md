---
title: "where can i download  jdk and jre?"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by r1e1z1a on 2009-03-09
where can i download jdk & jre for ubuntu 8.10?

This is the best forum i have ever seen.

thanks alot!!!!

---

### Post by Neo_The_User on 2009-03-09
Java JRE from official site: [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

Java JDK from official site: [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u12-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u12-oth-JPR@CDS-CDS_Developer)

Use the "Linux" one if you are not sure if you use an AMD64 processor.

PLEASE NOTE: YOU CAN USE THE SUN DOWNLOAD MANAGER! IT DOES EVERYTHING FOR YOU!

Java from repos:

Open up a terminal and copy and paste.

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk sun-java6-plugin

```

One more thing, if you're going to use the one from the java website, select the Linux (self-extracting file)  or for AMD64 use Linux x64. If unsure, use the Linux (self-extracting file)

---

### Post by r1e1z1a on 2009-03-09
Thanks Dear 
               "Neo_The_User"

but I can't download from sun(because of my Ip) 
and I can't connect to internet with my UBUNTU to use add/remove etc..
(because ubuntu didn't recognize my modem)
i should download jdk from windows then install in my ubuntu os.

please tell me a good site for downloading jdk & jre.

thank you very very much; my friend!

---

### Post by Neo_The_User on 2009-03-09
What version of ubuntu are you using? Then I can get you the .deb packages you can download on your windows computer then save to a flash drive then install via gdebi.

---

### Post by r1e1z1a on 2009-03-10
UBUNTU 8.10

with special thanks!!

---

### Post by jespdj on 2009-03-10
You can download the packages manually from [http://packages.ubuntu.com](http://packages.ubuntu.com)

Look for sun-java6-jdk. Note that you will have to download all the packages that the JDK package depends on.

---

