---
title: "tomcat login problem"
date: 2008-10-19
forum: General Help
---

### Post by charanpreethu on 2008-10-19
I am unable to login to tomcat.If I type tomcat for both username and password it says the usernme or password is wrong.what am i supposed to do?

---

### Post by praxis1949 on 2008-10-20
If you are using the version of Tomcat that comes with Ubuntu, I would seriously consider reloading Tomcat from the Apache-Tomcat site, and set it up yourself. "garylai posted excellent (and easy to follow) instructions entitled "Tomcat 6 installation guide for Feisty" ( see [http://ubuntuforums.org/showthread.php?t=420034 ]("http://ubuntuforums.org/showthread.php?t=420034")).  Your problem probably lies with the tomcat-users.xml file, but the ubuntu installation has at least three different versions of this file (seems to have about three different versions of everything). Causes inordinate grief.

Regards

John S
Gatineau, QC, Canada

---

### Post by praxis1949 on 2009-01-02
> **charanpreethu said:**
> I am unable to login to tomcat.If I type tomcat for both username and password it says the usernme or password is wrong.what am i supposed to do?

I asume you are talking about logging into the "manager" and "administration" functions.

Modify "tomcat-users.xml", which in my system is found in "usr/share/tomcat6/conf". Check what is found under "user-username". 

It should look like this when finished:

  <?xml version="1.0" encoding="utf-8" ?> 
- <tomcat-users>
  <role rolename="manager" /> 
  <role rolename="admin" /> 
  <user username="anyName" password="anyPassword" roles="admin,manager" /> 
  </tomcat-users>

In the repository version of Tomcat, I am not sure where the applicable tomcat-users.xml is (there may be a number versions under different directories).

 BTW, you may have to change this file's ownership (I think originally it was owned by root) before modifying it.

Good luck


J. Smith

---

