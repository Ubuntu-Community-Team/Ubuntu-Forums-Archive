---
title: "java package downloaded but still required"
date: 2008-08-26
forum: General Help
---

### Post by A117 on 2008-08-26
i downloaded sun-java6-bin_6-06-0ubuntu1_i386.deb and sun-java6-jre_6-06-0ubuntu1_all.deb
but when i install them (double click), it's said they are still needed to be downloaded. why?:confused:

---

### Post by aloshbennett on 2008-08-26
You could avoid all that trouble by using
> apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by A117 on 2008-08-26
i'm avoiding auto download, since i cannot control bandwidth that way.
when installing sun-java6-bin, it requires sun-java6-jre and sun-java6-bin.
when installing sun-java6-jre, it requires these two, too.

---

### Post by aloshbennett on 2008-08-26
How bout calling dpkg -iR and passing all the packages together, hoping dpkg would figure out the dependency?

---

### Post by A117 on 2008-08-26
> **aloshbennett said:**
> How bout calling dpkg -iR and passing all the packages together, hoping dpkg would figure out the dependency?

magic. magic.
a million of thanks aren't enough.

---

