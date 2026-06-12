---
title: "java"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by pat boy on 2009-07-28
i can don't download java ?? can some one help me do this plz ?

it downloads but can not run as i have no thing to run it look like

---

### Post by Mighty_Joe on 2009-07-28
Can you give us some more information, like exactly what you are attempting to do, exactly what you expect to happen and exactly how what happened differed from your expectations?

---

### Post by pat boy on 2009-07-28
> **pat boy said:**
> i can don't download java ?? can some one help me do this plz ?

it downloads but can not run as i have no thing to run it look like

i am trying to download java to play a onli game called runesacap, but when i down load it it comes up on dest top as a word like thing and will not run at all

---

### Post by baizon on 2009-07-28
Check this site: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by pat boy on 2009-07-28
/home/patrick/Desktop/jre-6u14-linux-x64-rpm.bin
/home/patrick/Desktop/jre-6u14-linux-i586-rpm.bin 
this is how they come up when i down load them and they don't work

---

### Post by Mighty_Joe on 2009-07-28
> **pat boy said:**
> i am trying to download java to play a onli game called runesacap, but when i down load it it comes up on dest top as a word like thing and will not run at all

So you went to the Sun Java site and downloaded the Java runtime?  Probably a bad idea.  
Follow the link baizon posted.  Install the Java runtime with Add/Remove Programs, Synaptic or apt-get then use "sudo update-java-alternatives" to set Sun Java as the default for your system.

---

### Post by pat boy on 2009-07-28
what do you mean by a bad idea ???

---

### Post by Mighty_Joe on 2009-07-28
First, as you've discovered, it is difficult to install the binary Java package.  Second, installing the binary package can work, but it would not be maintained in the Ubuntu repository, so if a critical bug or exploit were discovered with the version you have, you would not receive a fix via Ubuntu's update feature.  
When in doubt, use Add/Remove Programs, Synaptic or apt-get.

---

