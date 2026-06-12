---
title: "help with sudo apt-get install"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by brandon19 on 2009-10-14
Im new to ubuntu and i want to use the g++ compiler so that i can compile my c++ code. The problem is that whenever i try to use the sudo apt-get install command i always get told that the package cannot be found. Can anyone help me out with this? What am i doing wrong?

---

### Post by junke1990 on 2009-10-14
```
 sudo aptitude search g++
``` ;-)

hopefully this will help you

```

junke@junke-eee:~$ sudo aptitude search g++ |grep g++
i A g++                             - The GNU C++ compiler                      
p   g++-4.1                         - The GNU C++ compiler                      
p   g++-4.1-multilib                - The GNU C++ compiler (multilib files)     
p   g++-4.2                         - The GNU C++ compiler                      
p   g++-4.2-multilib                - The GNU C++ compiler (multilib files)     
i A g++-4.3                         - The GNU C++ compiler                      
p   g++-4.3-multilib                - The GNU C++ compiler (multilib files)     
p   g++-multilib                    - The GNU C++ compiler (multilib files)     
p   ppu-g++                         - PPU C++ compiler                          
p   spu-g++                         - SPU cross-compiler (C++ compiler) 

```

---

### Post by geurt on 2009-10-14
Hi there, 
Here is your answer:
use:

```
apt-cache search application
```

where "application" can be a part of the package name.

A good choice that your needed package is listed in the output.

---

### Post by Dougie187 on 2009-10-14
Or you could just do
```
sudo apt-get install build-essential
```

That will install most of the common programming utilities.

---

### Post by deeph on 2009-10-14
thanks... coz i have same problem

---

### Post by brandon19 on 2009-10-14
Hey, thanks guys i tried both commands and i found all other packages except the g++. Anyone else have any advice?

---

### Post by brandon19 on 2009-10-14
hey just tried the build-essential and i got a return message stating that the package could not be found

---

### Post by blur xc on 2009-10-14
> **brandon19 said:**
> hey just tried the build-essential and i got a return message stating that the package could not be found


Is there something wrong with your sources.list?

BM

---

### Post by brandon19 on 2009-10-14
> **blur xc said:**
> Is there something wrong with your sources.list?

BM
im not sure. How would i know?

---

### Post by blur xc on 2009-10-14
> **brandon19 said:**
> im not sure. How would i know?


```
cat /etc/apt/sources.list
```and post the results.

BM

edit- what happens when you do a sudo apt-get update?

---

### Post by brandon19 on 2009-10-14
ok so i ran the sudo apt-get update command and my computer spit out a bunch of jargon then opened update manager automatically. I am now in the process of updating so thank you very much for the updates i hope this solves the bigger problem. Can i use this command to  get like monthly updates?

---

### Post by blur xc on 2009-10-14
> **brandon19 said:**
> ok so i ran the sudo apt-get update command and my computer spit out a bunch of jargon then opened update manager automatically. I am now in the process of updating so thank you very much for the updates i hope this solves the bigger problem. Can i use this command to  get like monthly updates?

There's a setting somewhere in the update manager that controls at what interval it automatically checks for updates.  See if you ahve that enabled, or if you have automatic updates disabled.

apt-get update updates the cache on your local machine of what software is available on the repositories.  apt-get upgrade installs new versions of software and additional security patches.  apt-get dist-upgrade (I think) upgrades you distro to the new version, ie. 9.04 to 9.10.  You should always run apt-get update before you do an apt-get install.  Also, save yourself some typing- add

alias update="sudo apt-get update"
alias upgrade="sudo apt-get upgrade"
alsia install="sudo apt-get install"

etc... to your .bashrc...

see [http://crunchbanglinux.org/forums/topic/1093/post-your-bashrc/](http://crunchbanglinux.org/forums/topic/1093/post-your-bashrc/) for more...

BM

---

### Post by brandon19 on 2009-10-14
hey thanks. Ill let you know if this solves my problems with the g++ compiler

---

### Post by brandon19 on 2009-10-14
Hey I dont really understand the alias. I get what is going on, your just creating a shortcut word for a command, but im really new at all this could you kinda walk me through it. Where do i type alias upgrade = "sudo apt-get upgrade"?

---

### Post by brandon19 on 2009-10-14
the update worked and my g++ compiler works now. Thanks guys

---

### Post by blur xc on 2009-10-15
> **brandon19 said:**
> Hey I dont really understand the alias. I get what is going on, your just creating a shortcut word for a command, but im really new at all this could you kinda walk me through it. Where do i type alias upgrade = "sudo apt-get upgrade"?
 

Aliases are shortcut words for common command line commands.  They save you a lot of time.

It's in your /home/<username>/.bashrc file.

Just type in *gedit ~/.bashrc* and have at it.  Check that link out in my other post, just copy paste some of their aliases in. 

BM

---

### Post by geoffLW on 2009-10-15
I have a very similar problem... just in reverse.
I tried to load a package called Graphite ONe a CAD package.
The idea is that you load it with the debian loader but when I try that I find that I get a message box telling me that another software loader is running.  I can't find one that I recognise in 'System Monitor'
Is there sompelace I can stop 'aptitude' or similar loading at boot or can I switch it off via 'sudo'?

---

