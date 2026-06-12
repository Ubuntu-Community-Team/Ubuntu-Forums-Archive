---
title: "Java On Ubuntu Questions!"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by ffcfoo on 2009-07-06
Hi, I was just following this tutorial: [http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

I had a question: 

1. The part I completly do not get is "Setup the environment variable" I do not no what to do or how to do it? That is the only thing I am having trouble on!

---

### Post by darolu on 2009-07-06
Try the easy way and just install with Synaptic. I think the ubuntu-restricted-extras package has it; but I'm not completely sure, try it (sudo apt-get install ubuntu-restricted-extras) if it doesn't have it install java6-runtime with "sudo apt-get install sun-java6-jre" or look for it on Synaptic and should work.

Ubuntu by default, doesn't create a .bash_profile file; so if you want to do that you will have to edit the /etc/profile file adding the two lines the tutorial say; if you don't have vi or vim you can use gedit or nano.

---

### Post by ffcfoo on 2009-07-06
> **darolu said:**
> Try the easy way and just install with Synaptic. I think the ubuntu-restricted-extras package has it; but I'm not completely sure, try it (sudo apt-get install ubuntu-restricted-extras) if it doesn't have it install java6-runtime with "sudo apt-get install sun-java6-jre" or look for it on Synaptic and should work.

Ubuntu by default, doesn't create a .bash_profile file; so if you want to do that you will have to edit the /etc/profile file adding the two lines the tutorial say; if you don't have vi or vim you can use gedit or nano.

I did. I installed Java Runtime by typing: "sudo apt-get install sun-java6-jre" In termenal and it gave me this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 151 not upgraded.

```

EDIT: I already installed all the stuff in syntimatic.

---

### Post by darolu on 2009-07-06
Yeah that means you already have installed Java runtime; did you try:

```
sudo nano /etc/profile
```
or
```
gksudo gedit /etc/profile
```

to add the lines that website mentioned?

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun

export PATH=$PATH:$JAVA_HOME/bin
```

According to that tutorial by doing this you should be ready to write and compile java.

---

### Post by ffcfoo on 2009-07-06
> **darolu said:**
> Yeah that means you already have installed Java runtime; did you try:

```
sudo nano /etc/profile
```or
```
gksudo gedit /etc/profile
```to add the lines that website mentioned?

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun

export PATH=$PATH:$JAVA_HOME/bin
```According to that tutorial by doing this you should be ready to write and compile java.

Where do I add the lines at? Like where in the /etc/profile do I edit?

---

### Post by darolu on 2009-07-06
The safest place would be at the very end.

But I'm not sure doing all the tutorial say is necessary, first it seems the tutorial is for "Ubuntu Linux 7.10", so if you are using a different version it is possible the instructions are no longer needed; also seems to be aimed for people who have more than one java re, like sun-java, openjdk or the default-jre, etc.

Have you tried to use, write and compile a Java app and see if it is giving you any problem?

---

