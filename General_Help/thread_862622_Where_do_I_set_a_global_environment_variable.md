---
title: "Where do I set a global environment variable?"
date: 2008-07-17
forum: General Help
---

### Post by matthewboh on 2008-07-17
I've been trying to get some software running, and apparently I ran something along the way that sets JAVA_HOME to point to the 1.5 installation.  I want it to point to Java 6

I've run ```
export JAVA_HOME=/usr/lib/jvm/java-6-sun
``` and I've run the update-java-alternatives, and sudo update-alternatives --config java but still, every time I log back onto the machine, JAVA_HOME is set to

/usr/lib/jvm/java-1.5.0-sun

but if I type 

java -version

it comes back with

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

I've checked my .profile, my .bashrc, /etc/bash.bashrc, and /etc/profile and I don't know where else to look.  Can anyone help?

---

### Post by Dr Small on 2008-07-17
Add the command you mentioned to your .bashrc

---

### Post by ibutho on 2008-07-17
Global variables are set in /etc/environment. For individual users, you can set them in ~/.bash_profile.

---

### Post by ThinkProgramming on 2008-07-17
As i was searching last night for the same problem, I found everybody suggesting to edit a different configuration sort of files in ubuntu. But as i wanted to look into the things to be sure, found this

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

Very detailed description to which file should you edit, in which case.

---

### Post by matthewboh on 2008-07-17
Thanks!

---

