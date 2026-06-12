---
title: "Does anyone know how to install the latest version of java for ubuntu 8.10?"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by Pedro D on 2009-03-02
I need java so I can play RuneScape. Anybody know how to install it?

---

### Post by taurus on 2009-03-02
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Pedro D on 2009-03-02
Ok what do I do next?

---

### Post by Pedro D on 2009-03-02
I'm Waiting....

---

### Post by taurus on 2009-03-02
Reboot.  Then, log back in.  Now, open a terminal and post the output of this command.

```
java -version
```

---

### Post by Pedro D on 2009-03-02
This is what showed up.


pdesousa@pdesousa-desktop:~$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * jamvm
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
pdesousa@pdesousa-desktop:~$

---

### Post by Pedro D on 2009-03-02
What do I do now?

---

### Post by taurus on 2009-03-02
What is the output of this command?

```
sudo apt-get install sun-java6-jre
```

---

### Post by Pedro D on 2009-03-02
At the bottom that says if I want to continue I selected yes. I pressed the "Y" bottom on the keyboard and pressed "ENTER"



pdesousa@pdesousa-desktop:~$ sudo apt-get install sun-java6-jre
[sudo] password for pdesousa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin unixodbc xutils-dev
Suggested packages:
  equivs sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts libmyodbc
  odbc-postgresql libct1
The following NEW packages will be installed:
  gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  unixodbc xutils-dev
0 upgraded, 7 newly installed, 0 to remove and 221 not upgraded.
Need to get 35.3MB of archives.
After this operation, 103MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by Pedro D on 2009-03-02
It's almost finished now.

---

### Post by taurus on 2009-03-02
Are you running x86_64?

```
lsb_release -a
uname -a
```

---

### Post by Pedro D on 2009-03-02
It finished and now it is on a page talking about some terms and conditions. What am I sopose to do there?

---

### Post by Pedro D on 2009-03-02
What do you mean by x86_64?

---

### Post by taurus on 2009-03-02
You need to accept the java license agreement.  Press the Tab key to highlight the <OK> and Return to accept it.

---

### Post by Pedro D on 2009-03-02
Ok I did what you said. At the end it says:

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
pdesousa@pdesousa-desktop:~$ 

Does that mean it is done?

---

### Post by Pedro D on 2009-03-02
I guess it does.

---

### Post by Alex82 on 2009-03-02
Hello I am having a similar problem but on ubuntu 8.04. I have a AMD turion 64X2 processor in a compaq V3000.

I am a complete noob and have managed to install java6 (i think) but can not get any plugins to work. I have been through lots of forum pages and tried allsorts but with no avail 

any help would be greatly appriciated

---

### Post by taurus on 2009-03-02
> **Alex82 said:**
> Hello I am having a similar problem but on ubuntu 8.04. I have a AMD turion 64X2 processor in a compaq V3000.

I am a complete noob and have managed to install java6 (i think) but can not get any plugins to work. I have been through lots of forum pages and tried allsorts but with no avail 

any help would be greatly appriciated

Are you running the x86 or x86_64 version on your machine?

```
uname -m
```
i686 = 32bit
x86_64 = 64bit

---

### Post by Alex82 on 2009-03-02
alex@alex-laptop:~$ uname -m
x86_64

64

---

### Post by taurus on 2009-03-02
Don't believe there is a java plugin for x86_64 unless you want to go with the beta.  However, open synaptic and **Search** for sun-java6 and see if the plugin is on the list.

---

### Post by Alex82 on 2009-03-02
there is no plugin listed

---

### Post by taurus on 2009-03-02
So you either have to use 32bit version of firefox (you need to install ai32-libs first before you can run 32bit apps in 64bit environment) or you need to head over to Sun's site and look for the beta of java (including plugin) for x86_64.

---

### Post by Alex82 on 2009-03-02
Ok I have previously downloaded the file from suns site to my computer but when i try to open the pacage to install i get the error:

Dependancy is not satisfiable: sun-java-6bin

---

