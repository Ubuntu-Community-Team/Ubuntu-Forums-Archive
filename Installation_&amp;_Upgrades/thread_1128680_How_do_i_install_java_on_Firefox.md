---
title: "How do i install java on Firefox"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by bineoner on 2009-04-17
Help i wana play runescape....can someone help me step by step 
Thank You

ubuntu 8.10

---

### Post by tommcd on 2009-04-17
To install the java runtime enviornment and the java plugin for firefox, open a terminal (applications > accessories > terminal) and run:
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
```
Or search for those packages in synaptic package manager and install them from there. Then restart firefox.

---

### Post by bineoner on 2009-04-17
> **tommcd said:**
> To install the java runtime enviornment and the java plugin for firefox, open a terminal (applications > accessories > terminal) and run:
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
```
Or search for those packages in synaptic package manager and install them from there. Then restart firefox.

ok ima try it now

---

### Post by bineoner on 2009-04-17
It doesnt work it said i still need to install java

---

### Post by tommcd on 2009-04-17
> **bineoner said:**
> It doesnt work it said i still need to install java

Are you talking about this game:
[http://runescape.com/](http://runescape.com/)
It works on my laptop. I didn't bother creating an account on that site; but the game loads without problems. I installed java on my computer exactly as I instructed you in my last post. What did you do to install java? Post the commands you used. Did you restart firefox?
Open a terminal and post the output of:
```
aptitude search sun-java6
```
If you installed java as I instructed it should look like this:
```

tom@ubuntu:~$ aptitude search sun-java6
i A sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-demo                  - Sun Java(TM) Development Kit (JDK) 6 demos
p   sun-java6-doc                   - Sun JDK(TM) Documention -- integration ins
p   sun-java6-fonts                 - Lucida TrueType fonts (from the Sun JRE)  
p   sun-java6-javadb                - Java(TM) DB, Sun Microsystems' distributio
p   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
i   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-plugin                - The Java(TM) Plug-in, Java SE 6           
p   sun-java6-source                - Sun Java(TM) Development Kit (JDK) 6 sourc
tom@ubuntu:~$ 

```
Notice the "i" in front of: sun-java6-jre, sun-java6-bin, and sun-java6-plugin. The "i" means they are installed. A "p" before the package means it is not installed.

---

### Post by bineoner on 2009-04-17
ok i put in the 1st code you gave me and this is what it said




ubuntu@ubuntu:~$ aptitude search sun-java6
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

### Post by 73ckn797 on 2009-04-17
If you followed the previous instructions it should work. Did you restart the system after installation?

---

### Post by bineoner on 2009-04-17
im running on a live cd cause my computer wont install ubuntu....cause i dont have anything on my computer cause ubuntu deleted windows so im running it on a live cd..

---

### Post by tommcd on 2009-04-17
When you ran ```
aptitude search sun-java6
``` was there no output at all? If there was please post it here.
The instructions I gave you should install java:
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Java_Runtime_Environment_.28JRE.29_for_Firefox_plug-in](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Java_Runtime_Environment_.28JRE.29_for_Firefox_plug-in)
Is this a Wubi install? Or did you install Ubuntu the real way onto a partition on your hard drive?

Also, check if you have all the repositories enabled. Go to: system > administration > software_sources. Make sure you have the universe and multiverse repositories enabled. 

Also, are you running 64 bit Ubuntu? The sun-java6-plugin is only available for 32 bit Ubuntu:
[http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=intrepid&section=all)

---

### Post by 73ckn797 on 2009-04-18
> **tommcd said:**
> When you ran ```
aptitude search sun-java6
``` was there no output at all? If there was please post it here.
The instructions I gave you should install java:
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Java_Runtime_Environment_.28JRE.29_for_Firefox_plug-in](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Java_Runtime_Environment_.28JRE.29_for_Firefox_plug-in)
Is this a Wubi install? Or did you install Ubuntu the real way onto a partition on your hard drive?

Also, check if you have all the repositories enabled. Go to: system > administration > software_sources. Make sure you have the universe and multiverse repositories enabled. 

Also, are you running 64 bit Ubuntu? The sun-java6-plugin is only available for 32 bit Ubuntu:
[http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=intrepid&section=all)

I have Java installed via repos on Jaunty 64 Bit and everything works fine.

---

### Post by tommcd on 2009-04-18
> **73ckn797 said:**
> I have Java installed via repos on Jaunty 64 Bit and everything works fine.
The OP is using Intrepid. The package for Intrepid only says i386. I don't know if that will work on 64 bit:
[http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=intrepid&section=all)
The package for Jaunty says amd64 i386:
[http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=sun-java6-plugin&searchon=names&suite=jaunty&section=all)

---

### Post by tommcd on 2009-04-18
> **bineoner said:**
> im running on a live cd cause my computer wont install ubuntu....cause i dont have anything on my computer cause ubuntu deleted windows so im running it on a live cd..
I have never tried to enable java from the live CD. That is likely your problem though.  
There is a feature called "live CD persistence" that is said to work on Intrepid:
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
You will need a usb flash drive for that.

Why can't you install Ubuntu? Perhaps we should work on that instead. Then java will be easy. Check the live CD for defects from the menu when you boot it up. If it passes the check, then try and install it. If you have nothing on your computer right now, then you have nothing to loose. If the install fails, then consider starting a new thread and post the specific problems you encounter. Use the 32 bit version of Ubuntu.

---

