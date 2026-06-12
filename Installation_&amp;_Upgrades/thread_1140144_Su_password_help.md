---
title: "Su password help"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Master0fWar on 2009-04-27
Alright I've looked at as many threads as I could about this problem and I couldn't find a solution for me. I'm a new Linux user, this is my first installation, and I decided to go with Ubuntu. Now, when trying to install something using the "su" command, it asks for the password, I input the password, no masking asterisks or anything show up, which I read was normal, but when I hit enter it takes me to a new line, I wait about 1 second and it says "su: Authentication failure". I do not have any experience installing files in Ubuntu, I was reading off a guide to install Java. Any help or tips would be greatly appreciated.

---

### Post by oldos2er on 2009-04-27
Ubuntu disables the root account by default. Use "sudo" in place of "su", or you can use "sudo su".

---

### Post by ddrichardson on 2009-04-27
To expand on that, rather then type ```
su
```to login as the root user, type "sudo" before the command you want:```
sudo ls /
```

---

### Post by Niniel on 2009-04-27
What are you trying to install?
The best/easiest way to install things in Ubuntu is to use Synaptic: System/Administration/Synaptic Package Manager. I would strongly recommend looking there first before you try to install something from other sources.

Some people prefer to do "gksudo program name", then you get a graphical prompt to enter your password.

---

### Post by Master0fWar on 2009-04-27
> **Niniel said:**
> What are you trying to install?
The best/easiest way to install things in Ubuntu is to use Synaptic: System/Administration/Synaptic Package Manager. I would strongly recommend looking there first before you try to install something from other sources.

Some people prefer to do "gksudo program name", then you get a graphical prompt to enter your password.

I am trying to install Java. I looked in the Synaptic Package Manager and installed the java runtime environment, should I install all of the Java applications?

EDIT: I got Java working, thanks for the help and quick responses.

---

