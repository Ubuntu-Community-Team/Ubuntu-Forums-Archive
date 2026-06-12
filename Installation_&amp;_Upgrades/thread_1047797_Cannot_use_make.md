---
title: "Cannot use make"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by atwin on 2009-01-22
Hello,

I am trying to install a program and I am getting the following error after I execute ./configure

configure: error: cannot find libreadline headers

I also can't execute the commands make and gmake!!!  How can I install these missing libraries!  I can't find their proper names!

Thanks in advance for your help,


atwin

---

### Post by taurus on 2009-01-22
What program are you trying to install?

---

### Post by lloyd_b on 2009-01-22
> **atwin said:**
> Hello,

I am trying to install a program and I am getting the following error after I execute ./configure

configure: error: cannot find libreadline headers

I also can't execute the commands make and gmake!!!  How can I install these missing libraries!  I can't find their proper names!

Thanks in advance for your help,


atwin

First step.  In a terminal window:
```
sudo apt-get install build-essential
```
This should get you all of the basic tools required to compile programs, including make.

Second step - In a terminal window again:
```
sudo apt-get install libreadline5-dev
```
This should install the development headers for the readline library, which is what it appears to be missing.

Do not be surprised if after installing this, the "./configure" errors out on a completely different library - it may take several "rinse and repeats" to get all the of requirements met (I *wish* a configure program could check for everything at once, instead of erroring out after the first "not found", but unfortunately they generally don't).

---

### Post by atwin on 2009-01-22
Nice thanks.  It worked.  I installed both of those.  But I can only use make!  Not gmake!?  Any ideas?  Oh by the way, I am trying to install netmate-meter.

After executing make, I am still getting errors.  That's why I want to install with gmake.  "Make" failed on FreeBSD but gmake installed the program properly.

---

