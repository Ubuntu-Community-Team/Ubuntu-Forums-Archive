---
title: "Problem accessing Tomcat 6 manager and host-manager webapp"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by swfchang on 2009-03-27
I´ve just installed my Ubuntu 8.10 server with LAMP server and Tomcat. I was able to see the page [http://localhost:8080](http://localhost:8080) and when I tried to access [http://localhost:8080/manager/html](http://localhost:8080/manager/html), it asked me for username and password which I have no clue what they were.

After searching on the forum, I followed the instructions to change /etc/tomcat6/tomcat-users.xml to add the roles and user as follows (I did not change the  commented lines in original file:

<tomcat-users>
<!--
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="role1" password="tomcat" roles="role1"/>
-->
  <role rolename=¨tomcat¨/>
  <role rolename=¨manager"/>
  <role rolename=¨admin¨/>
  <user username=¨tomcat¨ password=*mypassword* roles=¨tomcat,admin,manager¨/>
</tomcat-users>

I restarted tomcat using command sudo service tomcat6 restart

But when I tried to access [http://localhost:8080/manager/html](http://localhost:8080/manager/html) again, it timed out. After I commented out the lines I´ve added for the roles and users in the tomcat-users.xml file, I can access [http://localhost:8080/manager/html](http://localhost:8080/manager/html) again but it asked me for username and password again.

Not sure what else I needed to do to get it working. Appreciate if anyone out there could help.

Thanks a lot!

---

### Post by raulsan on 2009-04-25
I have exactly the same problem,
can anyone help?
thank you

---

### Post by ghetto2ivy on 2009-05-30
Sounds like an error in your xml. See this thread. Try the default one posted and see if it works for you.

[http://ubuntuforums.org/showthread.php?t=972911&highlight=tomcat6](http://ubuntuforums.org/showthread.php?t=972911&highlight=tomcat6)

---

### Post by HDave on 2010-01-25
I went around in circles with this to for a couple of hours and then realized, like the OP, I didn't delete the stupid XML comments that surround the sample roles and users!

---

### Post by jim.pishlo on 2010-02-09
[FONT=Arial Black][SIZE=7]DOH![/SIZE][/FONT]
I feel like such a noob!
The xml comments!

---

### Post by cjchand on 2010-03-03
Sweet mother of God. Total face-palm there :)

Many thanks, HDave!

---

### Post by armonr on 2010-05-12
Wow, I didn't even notice the comment lines, thanks :)

---

### Post by belano on 2010-06-26
Me neither, thanks for sharing

---

### Post by Wnutt on 2010-10-14
Kind of a stupid pitfall :oops:

Thanks guys...

---

### Post by bluehue on 2010-11-11
> **HDave said:**
> I went around in circles with this to for a couple of hours and then realized, like the OP, I didn't delete the stupid XML comments that surround the sample roles and users!
Unbelievable!! You wouldn't believe the things I had tried in 4 hours time to get it running. Thanks Dave! :guitar:

---

