---
title: "[SOLVED] OpenJDK installed, but no file association with .jar files"
date: 2008-08-21
forum: General Help
---

### Post by Alistair George on 2008-08-21
Can anyone advise why when I click a .jar file after installing openJDK I can only open it with jdk web start? It should be run as a Java application.

---

### Post by Alistair George on 2008-08-21
I answer my own question!
Reason was it had not installed icedtea-java7-jre , which you have to do with Synaptic manager under System Administration

Then you can type  java -jar (program I want to run).jar

Or 

Set run under .jar file properties.
Cheers,
Alistair.

---

