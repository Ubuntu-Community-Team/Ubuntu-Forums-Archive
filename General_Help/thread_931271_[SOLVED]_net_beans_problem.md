---
title: "[SOLVED] net beans problem"
date: 2008-09-27
forum: General Help
---

### Post by suhaib1thariq on 2008-09-27
i need to install netbeans in my system .........when i typed sudo apt-get get install netbeans5.5 it shows like this..

"suhaib@suhaib-desktop:~$ sudo apt-get install netbeans5.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  netbeans5.5: Depends: sun-java5-jdk but it is not going to be installed or
                        sun-java6-jdk but it is not going to be installed
               Depends: netbeans5.5-platform but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-13-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
"



what can i do...
how i can solve this and use netbeans

---

### Post by leg on 2008-09-27
It looks like the java jdk is not installed so find it in synaptic and checj it for installation and then re install netbeans.

---

### Post by tarun.winlin on 2008-09-27
> **suhaib1thariq said:**
> i need to install netbeans in my system .........when i typed sudo apt-get get install netbeans5.5 it shows like this..

"suhaib@suhaib-desktop:~$ sudo apt-get install netbeans5.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  netbeans5.5: Depends: sun-java5-jdk but it is not going to be installed or
                        sun-java6-jdk but it is not going to be installed
               Depends: netbeans5.5-platform but it is not going to be installed
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-13-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
"



what can i do...
how i can solve this and use netbeans

Can't you use 'aptitude install netbeans5.5', I thought aptitude is better suited for resolving any dependencies.
I am not sure though, you can give it a try.

---

