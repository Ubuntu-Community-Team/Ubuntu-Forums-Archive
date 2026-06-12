---
title: "Installing Eclipse J2EE"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by mastermind008 on 2009-10-01
I installed Eclipse using the repository on ubuntu Jaunty Jakalope. But I can't develop J2EE applications as J2EE module has not been installed. How can I upgrade my existing Eclipse installation to J2EE version?
:(

---

### Post by Mighty_Joe on 2009-10-01
Developing J2EE applications isn't dependent on one's IDE.  It is dependent on having access to a J2EE implementation (container, server, whatever).  Did you have a target in mind like JBoss, Glassfish, Weblogic, Geronimo, Websphere? Install one of those, point Eclipse to the J2EE JAR files the implementation provides and start coding.
Now, Eclipse has some tools that make it easier to develop J2EE apps.  You *may *be able to install them through Eclipse by clicking on Help->Install New Software and choosing whatever J2EE plugins you desire.

---

### Post by mastermind008 on 2009-10-01
Thanks for the kind attention!
But how can I locate those jar files?

---

### Post by Mighty_Joe on 2009-10-01
That depends on which J2EE container you install.

---

### Post by mastermind008 on 2009-10-04
I have installed tomcat 6 and glassfish. but Eclipse doesn't provide any option to create a web or enterprise application on ubuntu.

---

### Post by Mighty_Joe on 2009-10-05
> **mastermind008 said:**
> I have installed tomcat 6 and glassfish. but Eclipse doesn't provide any option to create a web or enterprise application on ubuntu.

Did you try clicking on Help->Install New Software and finding the J2EE plugin?  Which Eclipse package did you install?  "eclipse" or "eclipse-jdt"?  Definitely choose the latter.
Again, I'll reiterate that creating a J2EE application has no dependency on your code editor.  You could use [VI]("http://en.wikipedia.org/wiki/Vi") (and there are people who do). All that matters is making the J2EE implementation (Glassfish) accessible when you compile your code. 
[This page]("http://www.webagesolutions.com/knowledgebase/javakb/jkb005/index.html") shows how to add Glassfish JAR files to an Eclipse Java project. I haven't tried it, I use Tomcat or Weblogic, but it looks correct from my experience.

---

### Post by mastermind008 on 2009-10-05
Thank you very much Mighty_Joe for your kind attention.

That's what the problem I have. I installed eclipse from the ubuntu repository (Via sudo apt-get install eclipse), but always I tried to install J2EE plugins by "Help--->Find & Install" the download is broken on 57%. So can you tell me what Eclipse product we have on Ubuntu repository (Gallilio/Ganymade/Europa etc)? I downloaded WTP tools zip file separately and tried to install as an archived site. But It didn't let me to do that (Indicated that there is no any archived update site in that ZIP file.)

---

### Post by Mighty_Joe on 2009-10-06
> **mastermind008 said:**
> Thank you very much Mighty_Joe for your kind attention.

Not a problem :)

> **mastermind008 said:**
>  So can you tell me what Eclipse product we have on Ubuntu repository (Gallilio/Ganymade/Europa etc)? 

The package in the repository is 3.2.2-5ubuntu3.  If that corresponds to Eclipse 3.2.2, it's a pretty old version (Galileo is the current 3.5.x release).  You may be better off downloading the binary from Eclipse.org and unzipping it under your home directory (or a reasonable subdirectory, like $HOME/bin).

> **mastermind008 said:**
> 
I downloaded WTP tools zip file separately and tried to install as an archived site. 

I don't think plugins are distributed as "archived sites".  I think they're just the plugin files zipped up.  You'd just unzip them into Eclipse.  [This site]("http://agile.csc.ncsu.edu/SEMaterials/tutorials/install_plugin/index_v35.html#section2_0") seems to agree with my assessment.

---

### Post by mastermind008 on 2009-10-06
Thank you so much Mighty Joe.
Your advice really helped me to overcome my problem! I really do appreciate such generous people just like you!
:P

---

