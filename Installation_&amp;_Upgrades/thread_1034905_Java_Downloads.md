---
title: "Java Downloads"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by michael91 on 2009-01-09
When I try to download stuff from the Update Manager, it says that I have to "manually run 'dpkg --configure -a' to correct the problem." I open the Terminal, then type in:

sudo dpkg --configure -a

This then goes on to say that I have to download one of three archives: 

j2sdk-1_4_2-doc.zip, j2sdk-1_4_0-doc-ja.zip or j2sdk-1_4_2-doc-ja.zip

I go to [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html) (the site that it says to go to), however from there, I can't find those files; I can only find j2se files, such as "J2SE v 1.4.2_19  SDK". Are these equivalent files, or do I have to find others?

I am currently running Ubuntu 8.04.

---

### Post by Pumalite on 2009-01-09
Try:
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

Java is in Synaptic.

---

