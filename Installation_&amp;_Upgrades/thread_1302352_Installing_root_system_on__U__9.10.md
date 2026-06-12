---
title: "Installing root system on  U  9.10"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by samuraitor on 2009-10-27
Hi everyone,

I tried to install root system on Ubuntu 9.10 to set the root system .But I have failed  from synaptic and  from terminal. This is the message I get when trying to install the system:

root-system-bin:
 Depends: libroot5.18 but it is not going to be installed
 Depends: root-plugin-asimage but it is not going to be installed
 Recommends: root-plugin-gl but it is not going to be installed
 Recommends: libroot-minuit or
	root-fitter
 Recommends: libroot-dev but it is not going to be installed

How should I install it?

---

### Post by JBAlaska on 2009-10-27
Someone here could tell you....but then they would have to kill you...

Just say no to root...or google it LOL

---

### Post by samuraitor on 2009-10-27
> **JBAlaska said:**
> Someone here could tell you....but then they would have to kill you...

Just say no to root...or google it LOL


I am not getting anything on google for kamic koala.

---

### Post by Nepomuk on 2009-11-02
I have the same problem here, trying to install "root-system" on my Kubuntu 9.10 machine. The problem seems to be with a change of a packagename ("[libkrb53]("https://launchpad.net/ubuntu/karmic/lpia/libkrb53")" -> "[libkrb5-3]("https://launchpad.net/ubuntu/karmic/lpia/libkrb5-3")") and the not changing of the dependencies in the following packages:

```
The following packages have unmet dependencies:
root-plugin-krb5: depends on: libkrb53 (>= 1.6.dfsg.2) , which is a virtual package.
root-system-xrootd: depends on: libkrb53 (>= 1.6.dfsg.2) , which is a virtual package.
root-system-proofd: depends on: libkrb53 (>= 1.6.dfsg.2) , which is a virtual package.
root-system-rootd: depends on: libkrb53 (>= 1.6.dfsg.2) , which is a virtual package.
libroot5.18: depends on: libkrb53 (>= 1.6.dfsg.2) , which is a virtual package.
```(Since my Kubuntu is in German I have translated the error-massages, so it may differ a bit from the English version.)

I don't have any experience in modifying packages, so I would be glad, if someone finds a solution :)

---

### Post by maverickm on 2009-11-06
Hi, i installed 
[http://packages.ubuntu.com/intrepid/amd64/libkrb53/download](http://packages.ubuntu.com/intrepid/amd64/libkrb53/download)
manualy and then i could install root-system by using


sudo apt-get install root-system 

i you got a 32-bit system change the url ;)

---

### Post by Nepomuk on 2009-11-16
Thanks, maverickm, it works fine two times.

---

### Post by marcelo.g.jordao on 2009-11-16
Thanks maverickm, I had the same issue, and it's solved now!
Cheers

---

### Post by mahesh5263 on 2010-04-08
I am having same problem can any one tell me how can I install root-system-bin. How should I do it???????

---

