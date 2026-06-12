---
title: "Failed to load Main-Class manifest..."
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by Don Green on 2009-08-26
Having installed Saxon through Synaptic Package Manager... what next?
I make the terminal current directory = usr/share/java/saxonb9.0.jar
I execute the following line from terminal:
java -jar saxonb-9.0.jar
I receive error message: "Failed to load Main-Class manifest attribute from saxonb-9.0.jar"
Any suggestions?

---

### Post by Don Green on 2009-08-26
> **Don Green said:**
> Having installed Saxon through Synaptic Package Manager... what next?
I make the terminal current directory = usr/share/java/saxonb9.0.jar
I execute the following line from terminal:
java -jar saxonb-9.0.jar
I receive error message: "Failed to load Main-Class manifest attribute from saxonb-9.0.jar"
Any suggestions?
"Failed to load Main-Class manifest attribute from saxonb-9.0.jar"

---

### Post by Alex8080 on 2009-10-18
I had the same issue when installing Saxon through Synaptic Package Manager.
 I guess that there is a miscompiled version online in the repo (main-java file does not have a main-class defined)
 
 Use the original source instead: [http://saxon.sourceforge.net](http://saxon.sourceforge.net)

---

