---
title: "Gutsy java not finding new installation issue"
date: 2008-10-03
forum: General Help
---

### Post by Lyk4n on 2008-10-03
I'm running Gutsy and I used a .deb file to install java jre 6.0.0.7, however it installed it into /usr/java/ instead of /usr/jvm/ how do I tell the system to look for the new java version in that folder instead of the jvm folder? Thanks in advance!

---

### Post by jamesstansell on 2008-10-16
It should be possible to use the update-alternatives or update-java-alternatives commands but I'm not sure the exact options you would need.

Personally I would look into using the package from the hardy or intrepid archives.  I've done that successfully with other versions.

Or, depending on what you're using the JRE for, you might be able to use exactly what you have already with onlly a minimum of fuss.  But I would have to know more to make any suggestions.

---

