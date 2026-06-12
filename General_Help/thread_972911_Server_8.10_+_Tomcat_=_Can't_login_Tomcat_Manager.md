---
title: "Server 8.10 + Tomcat = Can't login Tomcat Manager"
date: 2008-11-06
forum: General Help
---

### Post by Dimas on 2008-11-06
Hi,

I've installed a Ubuntu 8.10 Server with the Tomcat preconfigured package. I can access to [http://remoteip:8080](http://remoteip:8080) and the "It works !" appears. In that page there are a link to the Tomcat Manger: [http://remoteip:8080/manager/html](http://remoteip:8080/manager/html) and a login request appears. No user can login.

I've edited /etc/tomcat6/tomcat-users.xml to add a new role:
<role rolename="manager"/>
And a user with that role:
<user username="tomcat" password="tomcat" roles="manager"/>
And another user to test:
<user username="test" password="test" roles="manager"/>
And restarted the server:
/etc/init.d/tomcat6 restart

But the problem is not solved, I can't access to Tomcat Manger :(

Any idea?

---

### Post by Dimas on 2008-11-06
Someone can move this post to the Server threat?

---

### Post by Dimas on 2008-11-07
nobody? :(

---

### Post by Nepherte on 2008-11-07
Try using one user instead and add others later on when it works. That makes it less complicated to test with.

I find it strange that you would only add the manager role to tomcat. Try this instead:
[html]
<?xml version='1.0' encoding='utf-8'?>
<tomcat-users>
  <role rolename="manager"/>
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="test" password="test" roles="manager"/>
  <user username="role1" password="tomcat" roles="role1"/>
</tomcat-users>[/html]

---

### Post by Dimas on 2008-11-07
Thx, solved :)

---

### Post by cyberdenz on 2008-11-12
Also had the same situation ...

The default tomcat-users.xml file:
<tomcat-users>
<!--
  <role rolename="tomcat"/>
  <role rolename="manager"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="both" password="tomcat" roles="tomcat"/>
  <user username="dennis" password="tomcat" roles="manager"/>
-->
</tomcat-users>

cause of the problem: I was not able to remove "<!--" and "-->":)

---

### Post by sbittante on 2009-02-18
> **cyberdenz said:**
> 
cause of the problem: I was not able to remove "<!--" and "-->":)

Don't worry, I wasn't able either! :-)

---

### Post by abendigo on 2009-02-21
> **sbittante said:**
> Don't worry, I wasn't able either! :-)

*smacks forehead* DOH! God, I feel like such a noob!

---

### Post by Darkmoon_UK on 2009-05-18
Thank you for beating me, cowering in n00by shame, with a big clue bat. <!-- I must be blind too -->

---

### Post by sanemanmad on 2010-03-02
Wow.... What a noob move, i have had better days :P . thanks for the help.

---

### Post by loedu on 2010-03-05
OMG, same thing happened to me just now, banged my head against the wall, makes me feel ashamed :-)

Thanks!

---

### Post by chmod0750 on 2010-04-20
[QUOT]

cause of the problem: I was not able to remove "<!--" and "-->"[/QUOTE]

Doh! Me too.:)

---

### Post by codewarrior2000 on 2011-05-20
Yep, I'm not a noob but I made the same bone-headed noob move. This forum saved me hours of craziness.

P.S. I don't remember Tomcat's tomcat-users.xml ever having commented out users right out-of-the-box!!!!

---

