---
title: "Gateway, Firewall, Contentfilter, LAMP, Java enabled"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by herrfledermaus on 2009-08-17
Hi there,

for the moment I'm using clarkconnect as a home server which is ok but I need a Java enabled server (LAMP, tomcat, ...). (I'm studying java, that's why)

I'm really thinking about using Ubuntu for that purpose since I heard so much "good news" about it. But before I head to my basement, just a few questions:

1. can Ubuntu handle 2 nics, one for my provider, one for the LAN?
2. can I use a filter (like dansguardian) on it?
3. LAMP won't be a problem, but what about Java (meaning JRE, tomcat and other extra's)

and last but not least:

4. how hard is it to install all of the things mentioned above? Not that I'm a linux noob, but I'm not an expert either...

thanks all for your help,

kind regards,

Herr Fledermaus

---

### Post by Mighty_Joe on 2009-08-18
> **herrfledermaus said:**
> 
1. can Ubuntu handle 2 nics, one for my provider, one for the LAN?


Yes.

> **herrfledermaus said:**
> 
2. can I use a filter (like dansguardian) on it?


[apparently]("https://help.ubuntu.com/community/Servers/DansGuardian")

> **herrfledermaus said:**
> 
3. LAMP won't be a problem, but what about Java (meaning JRE, tomcat and other extra's)


No problem, but if you are using Tomcat, you'll want the JDK. Tomcat requires the Java compiler to compile JSP's.

---

### Post by herrfledermaus on 2009-09-07
well it works, after lot's of tryouts ;-)

I have now an ubuntu lamp/gateway/dhcp server with tomcat, jdk6 and such...

But it ain't that easy because of the gateway. Still have to find out how to open and close, and of course, monitor those ports for the webserver. Sometimes, I want them open for the outside world, sometimes not.

But that's another issue...

---

