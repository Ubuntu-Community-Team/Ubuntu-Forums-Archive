---
title: "Is 4GB Ram worth it on 32bit?"
date: 2009-05-25
forum: Hardware
---

### Post by RD1 on 2009-05-25
I'm currently running 9.04 32bit on my Acer Aspire 9410. It is 32bit hardware. I have 2GB ram in "Dual Channel" configuration. (2x1GB) With the current low prices on ram, I was considering upgrading to 4GB (2x2GB). I realize my system will not be able to use the full 4GB and will only see ~3.5GB. I also realize I could move to 3GB by replacing 1 1GB chip with a single 2GB chip but, I want to retain the "Dual Channel" configuration.

Question: Is this upgrade worth it?

---

### Post by RD1 on 2009-05-25
BUMP: no one has an opinion?

---

### Post by Corelogik on 2009-05-25
It is my understanding that you wont be any worse off by going to the 3GB configuration since the system can't see/use more than that anyway.

---

### Post by crazyfuturamanoob on 2009-05-25
You can install 32bit Ubuntu server edition, which supports the 4Gb.

---

### Post by RD1 on 2009-05-25
> It is my understanding that you wont be any worse off by going to the 3GB configuration since the system can't see/use more than that anyway.

But then I would loose the speed advantage of Dual Channel memory.

> You can install 32bit Ubuntu server edition, which supports the 4Gb. 

Would this require a complete re-install?

---

### Post by RedSingularity on 2009-05-25
Yeah you would need a fresh install for the server addition.

---

### Post by xavierp94 on 2009-05-25
> **crazyfuturamanoob said:**
> You can install 32bit Ubuntu server edition, which supports the 4Gb.
Doesn't the server edition have a graphical user interface?

---

### Post by RedSingularity on 2009-05-25
> **xavierp94 said:**
> Doesn't the server edition have a graphical user interface?

Nope.  You need to install it.  Very easy though.

---

### Post by RD1 on 2009-05-25
What is the actual difference in the server edition that allows a 32bit system to utilize 4GB ram? 

Couldn't this be installed to a normal Ubuntu installation?

---

### Post by b6of12 on 2009-05-25
no but but it is easy all you have to do is log on
after the install in do this 
```
sudo apt-get install ubuntu-desktop
```have a coffee brake

reboot......done:grin:

best do this with a internet cord (aka cat5/5e/6 cord) sents wireless is a pane in less the drivers are all ready installed pluse you mite have a more stable you don't wont to have to reinstall some thing you just installed mane das that SUCKS!!!;)

---

### Post by Steelmourne on 2009-05-25
You don't need more memory than 3GB unless you're running multiple programs with heavy memory usage which isn't too likely on ubuntu. With 1GB of memory on my laptop the usage never has gone past 55%, even with multiple apps open across 3 different virtual desktops. 

Another great reason to delete vista which took 85% with 2 open apps with the same laptop. Essentially, you don't need that much memory. Yet.

---

### Post by ozzyprv on 2009-05-26
Is there anything known NOT to work @ server edition?

Sorry, I have a hard time believing the desktop install would be the only difference. I wish I knew that some time ago...

Anyway, this post has helped me a lot. Thanks.

---

### Post by rob2uk on 2009-05-26
> **Steelmourne said:**
> You don't need more memory than 3GB unless you're running multiple programs with heavy memory usage which isn't too likely on ubuntu. With 1GB of memory on my laptop the usage never has gone past 55%, even with multiple apps open across 3 different virtual desktops. 

Another great reason to delete vista which took 85% with 2 open apps with the same laptop. Essentially, you don't need that much memory. Yet.

The reason memory usage always seems high in Vista is because of the way it uses the memory that's available to it - [explanation here]("http://www.codinghorror.com/blog/archives/000688.html")

---

### Post by matthewbpt on 2009-06-03
You don't need to reinstall ubuntu server edition, all you need to do is install the server kernel and boot from it,

```
$ sudo apt-get update
$ sudo sudo apt-get install linux-headers-server linux-image-server linux-server
```

edit: then reboot of course!

---

### Post by munky99999 on 2009-06-03
4gigs of ram generally doesnt get used.

[http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html](http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html)

On the otherhand. >3gigs ram will be future ready.

---

