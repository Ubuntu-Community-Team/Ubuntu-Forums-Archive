---
title: "Java install hard to do   Is there a easier way?"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by gccradioscience on 2009-09-11
I think that the new upcoming release of Ubuntu 9.10 remix should already have Flash and Java installed already since they are very important for most web sites since alot of newbies and users and admins are having a tough time to install these 2 important plug ins.    I tried to install the latest java and when I tried to download it from the Package Manager and then install the java environment, and then it starts in the terminal to ask me to login as root.  Look,I don't have a root login and when I tried to login as root and my password, it did not work.   So right now when go test my java the java site detect my java as a early out of date install and it wants me to get a updated version.  The truth is that I do not want to do alot of coding or computer programming I just want to simply install the app and go about my business just like with windows.   Download the software or plugin, open up the file and click install and then close.   Not open up the file extract it and try to find the installation software in the file, which has a bunch of source code that I do not understand yet. When I learn from the book for dummies about linux programming I will 
start installing it the old fashioned way in the future.  :confused:

---

### Post by presence1960 on 2009-09-11
are you using 32 bit or 64 bit ubuntu?

I suggest you read [this]("http://linux.oneandoneis2.org/LNW.htm") first!

---

### Post by gccradioscience on 2009-09-12
I use 32 bit Ubuntu 9.04 Remix  Netbook Editon.   I have heard that my SR2010 NX has a AMD 64 bit processor in it I might the 64 bit version soon if I can find it.

---

### Post by running_rabbit07 on 2009-09-12
If you are running 32-bit, it is even easier. Just open a terminal and copy and paste this code. ```
sudo apt-get install ubuntu-restricted-extras
```You may ask, "why it is not already installed?" The answer is easy. It is copyrighted and has an EULA. Some people don't want or need Java installed. Why? Because some people don't use their system for the net. Like the link in the above post implies, "Linux is not Windows." Some people just want to be able to install whatever version of Java they want. 

While Ubuntu/Linux may seem hard at first, a little practice makes it easier. I am new to Linux my self and I find it fun to learn how to make it work.

---

### Post by ezsit on 2009-09-12
Open up Add/Remove Software, make sure Show is set to All Available Applications and type "restricted" in the search box. You will see the results and choose the appropriate choice for your version of Ubuntu (or Kubuntu, or Xubuntu, etc). This will install Java, Flash, and a bunch of other useful codecs you were used to having in Windows. It really isn't that hard once you know what to do. 

As for the absolute latest Java, why do you need that particular version? The one installed by Ubuntu is more than sufficient and very recent.

---

