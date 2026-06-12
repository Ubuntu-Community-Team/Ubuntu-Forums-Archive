---
title: "Java 1.5_05 installed, but browsers use older version"
date: 2005-11-17
forum: General Help
---

### Post by Jaylon on 2005-11-17
Hello guys.

I followed the Wiki instructions and downloaded and installed java from the Sun site. I have selected sun java as the default option. 

The first couple of times I went to the [Java test page]("http://www.java.com/en/download/help/testvm.xml") the applet showed the correct version, but no animation played. Now it's started showing Blackdown Java version 1.4_02 with a headless animation..

sudo update-alternatives --config java gives me the following. Sun Java is starred, but I don't know what the + next to the Blackdown one means. Has anyone got a solution for this?

Selection    Alternative
-----------------------------------------------
      1        /usr/lib/jvm/java-gcj/bin/java
      2        /usr/bin/gij-wrapper-4.0
 +    3        /usr/lib/j2se/1.4/bin/java
*     4        /usr/lib/j2re1.5-sun/bin/java

---

### Post by jliedeka on 2005-11-17
The star means Sun's is the current choice for java.  The plus means Blackdown has the highest priority.  If you were in automatic mode, thatr one would be chosen.

As for which one the browser finds, check you plugins directory for a java plugin.  For Firefox, see /usr/lib/mozilla-firefox/plugins (and possibly check /usr/lib/mozilla/plugins and /usr/lib/firebird/plugins, if applicable).  What you need is a symbolic link to (I'm guessing the path since I don't have 1.5) /usr/lib/j2re1.5sun/jre/plugin/i386/ns610-gcc32/libjavaplugin_oji.so.

Your best bet is to run the command:

locate libjavaplugin_oji.so

and make sure the right one is symbolically linked into your plugins directory. 

     Jim

---

### Post by pxgray on 2005-11-17
Jaylon,

Check the directory /usr/lib/mozilla-firefox/plugins.  There should be two files, one named libjavaplugin_oji.so and another named libjavaplugin.so.  Both of these are symbolic links.  Remove the file /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so and your problem should be solved.

pxgray

---

### Post by Jaylon on 2005-11-19
Thanks for that. Seems to be okay now, fingers crossed...

---

