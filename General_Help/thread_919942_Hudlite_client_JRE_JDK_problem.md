---
title: "Hudlite client JRE JDK problem"
date: 2008-09-14
forum: General Help
---

### Post by querent on 2008-09-14
Hopefully this is a dumb question...meaning there is an easy answer.

I'm trying to install a [Hudlite]("http://www.hudlite.org") client on my ubuntu machine.

Converted the hudlite client rpm to deb with alien, installed with dpkg -i.  All went well.  'cd'ed into the directory and tried to run 'start_HUD.sh' and got the following error message in an error window:

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run HUD. No Java virtual machine
was found after searching the following locations:
/usr/fonality/hud-lite/./jre/bin/java
'java' in your current PATH

'start_HUD.sh' has the following line:   PATH=$PATH:/usr/java/jre1.5.0_06/bin/ 

should i just find this 'jre' and stick it in that path?  or is there some way to do this through the ubuntu repositories?

thanks in advance!

---

### Post by aloshbennett on 2008-09-14
You are right. Find where the jre (1.5 or higher) is installed and point the PATH to the location of JRE's bin folder. Even better would be to add the java path to your environment's PATH variable.

I suspect you dont have JRE installed at all. If that's the case, installing these would solve your problem:

> sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

---

### Post by querent on 2008-09-15
Worked!  thanks.  i ran the apt-get install you recommended, found the jre directory (/usr/lib/jvm), and edited the shell script to point there instead.

thanks again.

---

