---
title: "Tomcat 6"
date: 2008-11-09
forum: General Help
---

### Post by Lex-Man on 2008-11-09
I want to try and use Tomcat 6.

But I can't seem to set it up correctly.

The shutdown.sh code throws an error.

Java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml (No such file or directory)

The file sever.xml is in .../skel/conf/server.xml

Also I have edited the 

tomcat-users.xml file so it reads

<tomcat-users>
<role rolename="manager"/>
<role rolename="admin"/>
<role rolename="tomcat"/>
<role rolename="role1"/>
<user username="LexMan" password="******" roles="admin,manager"/>
<user username="tomcat" password="tomcat" roles="tomcat"/>
<user username="both" password="tomcat" roles="tomcat,role1"/>
<user username="role1" password="tomcat" roles="role1"/>
<role rolename="manager"/>
</tomcat-users>

But I can't log into the admin page.

Can anyone help?

---

