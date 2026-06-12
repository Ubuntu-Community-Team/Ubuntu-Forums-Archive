---
title: "How can I install zend server"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by delphiexile on 2009-04-06
Hi every one,

I've added the zend rep to my source.list , there is no problem , the packages have been added to my synaptic. 

My problem is that I don't know which packages do I have to install to run Zend Server. I tried with zend-pe (as mentioned in developer website) and all its dependencies .

Installation succeeded but I don't know if this is the correct way to install , or there is another way. If what I've done was right can you tell me how to run it ? is it a GUI ?

and thank so so much!!

---

### Post by delphiexile on 2009-04-06
Is there anyone here !!!!!

---

### Post by vdoki on 2009-11-14
Check out this:
[http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm](http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm)

Although that's what I try to do on ubuntu server 9.10 virtual machine install, and I can't resolve the libkrb53 and libkrb5-3 conflict, but I keep trying.

---

### Post by vdoki on 2009-11-14
I have found two solutions for the libkrb53 problem.

The first may be a better one, but I haven't:
[http://www.durcommefaire.net/Php](http://www.durcommefaire.net/Php)
It is French, but the commands are visible, that's all I understood.

The not so nice but easier solution is to manually install this package:
[http://packages.ubuntu.com/jaunty/libkrb53](http://packages.ubuntu.com/jaunty/libkrb53)
I don't know the side effects of this, so don't do it if you don't know what exactly you are doing.

---

### Post by shaharatzend on 2009-11-16
Hi,

See [http://forums.zend.com/viewtopic.php?f=44&t=4062](http://forums.zend.com/viewtopic.php?f=44&t=4062) for some relevant tips. We're also in the process of releasing versio 4.0.6 of Zend Server (should be out shortly) that will have better support for 9.10.

Best regards,

Shahar
[Technical PM for Zend Server]

---

### Post by vdoki on 2009-11-17
Great! Tanks a lot.

> **shaharatzend said:**
> Hi,

See [http://forums.zend.com/viewtopic.php?f=44&t=4062](http://forums.zend.com/viewtopic.php?f=44&t=4062) for some relevant tips. We're also in the process of releasing versio 4.0.6 of Zend Server (should be out shortly) that will have better support for 9.10.

Best regards,

Shahar
[Technical PM for Zend Server]

---

