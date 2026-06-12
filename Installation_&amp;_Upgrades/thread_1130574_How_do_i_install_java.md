---
title: "How do i install java?"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by homedawg913 on 2009-04-19
i need help installing java for firefox, or just my whole computer.
i need it to play a game called runescape ([http://www.runescape.com](http://www.runescape.com)

ive tried doing different things but i cant get it to work since im new at ubuntu.

i tried doing this>

sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin

but i get this error>

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and when i try to run>

dpkg --configure -a

i get this>

dpkg: requested operation requires superuser privilege

if anyone can help me fix this and install java on my computer i will appreciate it :]

---

### Post by ptn107 on 2009-04-19
```
sudo dpkg --configure -a
```

---

### Post by homedawg913 on 2009-04-19
ok thanks :] that fixed one of my problems, now lets see if it will let me play the game, i just installed the java

---

### Post by homedawg913 on 2009-04-19
still doesnt work... i need serious help lol...

---

### Post by tommcd on 2009-04-20
Can you post the output of:
```
aptitude search sun-java6
```
It will list all java packages in the repos. There should be a letter "i" (for installed) in front of: sun-java6-jre, sun-java6-bin, and sun-java6-plugin.
If it does, then to verify that the java plugin is working in firefox, go here: [http://time.gov/](http://time.gov/) and click on any of the time zones to get the time. If java plugin is working that page should work.

Did you actually install Ubuntu, or are you running from the live CD, or Wubi in Windows?

---

### Post by homedawg913 on 2009-04-20
i will try that when i get home.

i dont need the ubuntu cd to run it, i deleted windows and put ubuntu cos of virus problems.

---

### Post by homedawg913 on 2009-04-20
homedawg@homedawg:~$ aptitude search sun-java6
p   sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-demo                  - Sun Java(TM) Development Kit (JDK) 6 demos
p   sun-java6-doc                   - Sun JDK(TM) Documention -- integration ins
p   sun-java6-fonts                 - Lucida TrueType fonts (from the Sun JRE)  
p   sun-java6-javadb                - Java(TM) DB, Sun Microsystems' distributio
p   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
H   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-plugin                - The Java(TM) Plug-in, Java SE 6           
p   sun-java6-source                - Sun Java(TM) Development Kit (JDK) 6 sourc
homedawg@homedawg:~$

---

### Post by homedawg913 on 2009-04-20
ok so i tried installing it again, and it gets to the configure screen for java, but i dont know what to do for that, like how do i click <ok> or how do i agree to it.

---

### Post by ken78724 on 2009-04-20
Hi, I also want to install java so I may participate in a webinar this week using Ubuntu 8.04.2 herron hardy 64AMD and to do my install using your guidance in lieu of JDK ([http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)) 
as I am dumbfounded by the options when I go there. I have the following out puts from my terminal: 
k78724@Kproductions:~$ aptitude search sun-java6
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
k78724@Kproductions:~$ sudo dpkg --configure -a
[sudo] password for k78724: 
k78724@Kproductions:~$ sudo dpkg --configure -a
k78724@Kproductions:~$ aptitude search sun-java6
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
k78724@Kproductions:~$ 2~k78724@Kproductions:~$ aptitude search sun-java6
bash: 2~k78724@Kproductions:~$: command not found
k78724@Kproductions:~$ E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
bash: syntax error near unexpected token `('
k78724@Kproductions:~$ E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
bash: syntax error near unexpected token `('
k78724@Kproductions:~$ E: The list of sources could not be read.
bash: E:: command not found
k78724@Kproductions:~$ k78724@Kproductions:~$ sudo dpkg --configure -a
bash: k78724@Kproductions:~$: command not found
k78724@Kproductions:~$ [sudo] password for k78724: 
bash: [sudo]: command not found
k78724@Kproductions:~$ k78724@Kproductions:~$ sudo dpkg --configure -a
bash: k78724@Kproductions:~$: command not found
k78724@Kproductions:~$ k78724@Kproductions:~$ aptitude search sun-java6
bash: k78724@Kproductions:~$: command not found
k78724@Kproductions:~$ E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
bash: syntax error near unexpected token `('
k78724@Kproductions:~$ E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
bash: syntax error near unexpected token `('
k78724@Kproductions:~$ E: The list of sources could not be read.
bash: E:: command not found
k78724@Kproductions:~$ k78724@Kproductions:~$ 
bash: k78724@Kproductions:~$: command not found
k78724@Kproductions:~$ 
sorry I made a mess and somehow caused terminal to duplicate its output. 
glad accept help treating me like a new user... 
Ken

---

### Post by homedawg913 on 2009-04-20
ok i restarted my computer, which gave me some ready to update files, 2 of which were java jre, and java bin. but i still dont hava java plugin.

homedawg@homedawg:~$ aptitude search sun-java6
i   sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-demo                  - Sun Java(TM) Development Kit (JDK) 6 demos
p   sun-java6-doc                   - Sun JDK(TM) Documention -- integration ins
p   sun-java6-fonts                 - Lucida TrueType fonts (from the Sun JRE)  
p   sun-java6-javadb                - Java(TM) DB, Sun Microsystems' distributio
p   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
i   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-plugin                - The Java(TM) Plug-in, Java SE 6           
p   sun-java6-source                - Sun Java(TM) Development Kit (JDK) 6 sourc



ok so i got it to install the plugin and now the game works, so thanks to everyone that helped me.

---

### Post by tamas305 on 2009-04-20
Open a terminal (Applications --> Accessories --> Terminal) and type

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

and let it run and agree to end-user liscense and it should install java runtime environment onto your computer. It also installs the plugin for firefox, I believe.

Good luck,
-tamas

---

### Post by tommcd on 2009-04-20
> **homedawg913 said:**
> homedawg@homedawg:~$ aptitude search sun-java6
p   sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-demo                  - Sun Java(TM) Development Kit (JDK) 6 demos
p   sun-java6-doc                   - Sun JDK(TM) Documention -- integration ins
p   sun-java6-fonts                 - Lucida TrueType fonts (from the Sun JRE)  
p   sun-java6-javadb                - Java(TM) DB, Sun Microsystems' distributio
p   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
H   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-plugin                - The Java(TM) Plug-in, Java SE 6           
p   sun-java6-source                - Sun Java(TM) Development Kit (JDK) 6 sourc
homedawg@homedawg:~$
According to that output you do not have java installed. The "p" before all the java packages means they are not installed. The "H" before sun-java6-jre means that the package is half installed; the install was interupted. See this:
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s02.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s02.html)
So reinstall java:
```

sudo apt-get install --reinstall sun-java6-jre
sudo apt-get install sun-java6-plugin

```
Then restart firefox. Then go to [http://time.gov/](http://time.gov/) and verify that the java plugin is working.
What version of Ubuntu are you running? Are you using 32 bit or 64 bit Ubuntu?

---

### Post by tamas305 on 2009-04-21
> **tommcd said:**
> According to that output you do not have java installed. The "p" before all the java packages means they are not installed. The "H" before sun-java6-jre means that the package is half installed; the install was interupted. See this:
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s02.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s02.html)
So reinstall java:
```

sudo apt-get install --reinstall sun-java6-jre
sudo apt-get install sun-java6-plugin

```
Then restart firefox. Then go to [http://time.gov/](http://time.gov/) and verify that the java plugin is working.
What version of Ubuntu are you running? Are you using 32 bit or 64 bit Ubuntu?

Does what version of Ubuntu you are running impact the install? Just curious.

-tamas

---

### Post by tommcd on 2009-04-21
> **tamas305 said:**
> Does what version of Ubuntu you are running impact the install? Just curious.

The 64 bit Java plugin is fairly new. 
[http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NjkyOQ)
From some of the searching I have done it may not always work as reliably as the 32 bit version.

---

### Post by bayvista on 2009-04-22
For those people who don't like struggling with the Terminal. you can easily install Java using Synaptic:

System/Administration/Synaptic
[enter your password]
Quick Search - sun-java6
Click the boxes for sun-java6-jre, sun-java6-plugin and sun-java6-bin
Click "Mark for installation"
Click "Apply"

When installation finishes, make sure that Firefox is shut down and restarted. Then Java should work.

---

