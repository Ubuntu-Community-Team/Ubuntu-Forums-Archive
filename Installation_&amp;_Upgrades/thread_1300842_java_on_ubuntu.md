---
title: "java on ubuntu?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by dbowlin17 on 2009-10-25
I have no real programming skils, but I hope to be able to install java on my ubuntu 9.04 machine. What version of java should i be downloading? and then how would i go about installing it? remeber, im super new (just transitioned from xp 2 days ago)

---

### Post by socool274 on 2009-10-25
As I understand there is an apt-get package that installs all the java things you will need. I am not quite sure which package it is. To compile it, after it has been installed, you will use the command "java" and "javac".

---

### Post by dbowlin17 on 2009-10-25
so wait, i install a package, then compile it? any ideas as to how I do it or what I need to do to get my java working?

---

### Post by oldos2er on 2009-10-25
```
sudo apt-get update && sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

---

### Post by Hosmion on 2009-10-25
@old Is that programming or having Java to use for games.

---

### Post by dbowlin17 on 2009-10-25
does anyone know if that thing that old posted was for developers? I want the java for games as said by hosmion

---

### Post by dbowlin17 on 2009-10-25
Alright, I used the code that old posted. but i then got to another screen where it said configuration, and there was no way to get out. so i exited it. then i used add/remove to add java. but it said that it failed. is anyone able to provide help?

---

### Post by oldos2er on 2009-10-25
To move around in the ncurses java configuration screen, use the Tab, arrow, and Enter keys.

---

### Post by dbowlin17 on 2009-10-25
this is the error message i got upon trying it: E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by vinutux on 2009-10-25
> **dbowlin17 said:**
> this is the error message i got upon trying it: E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

close all apt front ends like add/remove, update manger, synaptic, etc...before installtion from terminal

---

### Post by dbowlin17 on 2009-10-25
> **vinutux said:**
> close all apt front ends like add/remove, update manger, synaptic, etc...before installtion from terminal

i had all of my windows except for terminal closed and it still gave me the same error message.

---

### Post by 1nooodlse on 2009-10-25
sun-java6-jre is the runtime environment some programs need this to run
sun-java6-plugin is the browser plugin
sun-java6-jdk is the development kit

i reccomend sun-java6-plugin sun-java6-jre and sun-java6-fonts for everyone
and i reccomend the above and sun-java6-jdk to java developers

ps java isn't a good first programming language python ftw

---

### Post by dbowlin17 on 2009-10-25
I am looking to install the plugin and the jre. The issue i have is that i get E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 error codes such as the ones above when trying to use terminal. when i try to use the add/remove utility it says installation failed.

---

### Post by vinutux on 2009-10-25
> **dbowlin17 said:**
> I am looking to install the plugin and the jre. The issue i have is that i get E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 error codes such as the ones above when trying to use terminal. when i try to use the add/remove utility it says installation failed.

Try after a restart

---

### Post by dbowlin17 on 2009-10-25
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
tim@tim-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

those are my new error messages. please help.

---

### Post by oldos2er on 2009-10-25
You need to run that command with admin privileges; **sudo apt-get install -f**

---

### Post by dbowlin17 on 2009-10-25
I don't know what occurred other than i changed my permissions so i could do everything it offered. and then typed it in, then retyped the whole long thing from before and now it all works. thanks!!!

---

