---
title: "Java Install issues"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by kenji_03 on 2009-08-18
Firstly, thank you for your time.

I view this forum as the god of all things Ubuntu and sometimes forget to check the repositories first.  I installed Java using [this tip from the forums]("http://ubuntuforums.org/showthread.php?t=76702")

[COLOR=Red]The instructions above are dated, please do not use them.  Use the following instead: [/COLOR]
Execute one of the following:
**sudo apt-get install sun-java6-jdk** - For the JDK (Developer)
**sudo apt-get install sun-java6-jre** - For the JRE (User)

So now I have a terminal window with a bunch of legal stuff written in it and I don't know what exactly to do.  I cannot figure out how to close it, it looks like those old dos programs that gave you the legal mumbo jumbo in DOS, but again, I cannot figure out how to hit okay and move on.

Trying to close the window tells me there is a process still running in terminal, should I close it anyway?

---

### Post by Partyboi2 on 2009-08-19
Hi, sound like you need to accept the license agreement, try pressing "tab" then "enter" to accept.

---

### Post by altog33k on 2009-08-25
having the same issue Can someone help please?

altog33k@altog33k-desk:~$ sudo apt-get install sun-java6-jre
Password:
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
altog33k@altog33k-desk:~$

---

### Post by oldos2er on 2009-08-25
> **altog33k said:**
> having the same issue Can someone help please?

altog33k@altog33k-desk:~$ sudo apt-get install sun-java6-jre
Password:
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
altog33k@altog33k-desk:~$

 Not the same issue at all. In a terminal, run **gksu gedit /etc/apt/sources.list** and either comment out line 38 by adding a # at the beginning of the line, or delete line 38 entirely (to activate line numbers in gedit, hit Ctrl-I, type in 38).

---

