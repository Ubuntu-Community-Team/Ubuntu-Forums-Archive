---
title: "MySQL and Ubuntu"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by hbradshaw on 2009-04-09
Hello:

I have my laptop setup to dual boot between Windows XP and Ubuntu.

On Windows, I have MySQL installed.

I need to access to MySQL with Ubuntu as well.

Do I have to install another copy of MySQL within Ubuntu?

Is it possible to access the MySQL install that is on Windows?

If I have to make another install, is Ubuntu considered an "RPM-based Linux distribution"?

If so, where can I get the proper download file?

Thanks.

---

### Post by dgoosens on 2009-04-09
I have the same "issue"...

just install MySQL as explained here:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

then, go to the my.cnf file, open it and set the datasources to the same place as the Windows install...

just make sure your Windows HD is mounted when using MySQL...

---

### Post by _Purple_ on 2009-04-09
> **hbradshaw said:**
> Hello:

I have my laptop setup to dual boot between Windows XP and Ubuntu.

On Windows, I have MySQL installed.

I need to access to MySQL with Ubuntu as well.

Do I have to install another copy of MySQL within Ubuntu?

Is it possible to access the MySQL install that is on Windows?

If I have to make another install, is Ubuntu considered an "RPM-based Linux distribution"?

If so, where can I get the proper download file?

Thanks.


You have to install MySQL in Ubuntu and Ubuntu is a Debian based distribution. You can follow the steps given in the post above. You can either get the packages from:
System > Administration > Synaptic Package Manager

then select from the list and install

OR you can go to Applications > Accessories> Terminal and then type

```
sudo apt-get install *packagename* 
```

---

### Post by hbradshaw on 2009-04-09
Hello:

Thank you for the link.

I'm a newbie to all this dual boot concept.

I have a few questions.

One, where do I find the my.cnf file, in Windows or Ubuntu directories?  

Two, I do not know how to set the datasources to the same place as the Windows install.  Am I pointing to a specific directory/file?

Three, how do I mount my HD?  I've mounted Oracle databases but never a HD.

Fourth, if I read the install document correctly, I'm supposed to install Apache along with MySQL and PHP5.  Correct?  I'm using Ubuntu 8.10.  How do I download these files/packages to install?

Thanks for all the help.

---

### Post by hbradshaw on 2009-04-09
What are the names of the packages I need to install?

---

### Post by _Purple_ on 2009-04-10
> **hbradshaw said:**
> Hello:

Thank you for the link.

I'm a newbie to all this dual boot concept.

I have a few questions.

One, where do I find the my.cnf file, in Windows or Ubuntu directories?  

Two, I do not know how to set the datasources to the same place as the Windows install.  Am I pointing to a specific directory/file?

Three, how do I mount my HD?  I've mounted Oracle databases but never a HD.

Fourth, if I read the install document correctly, I'm supposed to install Apache along with MySQL and PHP5.  Correct?  I'm using Ubuntu 8.10.  How do I download these files/packages to install?

Thanks for all the help.

Your .cnf file will be in Ubuntu directories /etc/mysql/my.cnf.
Take a look at [this](http://www.howtoforge.com/ubuntu_lamp_for_newbies) tutorial. It might be easier for you to follow.
In case you want to point to a directory in windows partition, you can check [here](http://ubuntuforums.org/showthread.php?t=133715) how to mount a partition in hdd.

---

### Post by dgoosens on 2009-04-10
> Fourth, if I read the install document correctly, I'm supposed to install Apache along with MySQL and PHP5. Correct? I'm using Ubuntu 8.10. How do I download these files/packages to install?

if you are only using MySQL, you do not need to install Apache or PHP...

---

