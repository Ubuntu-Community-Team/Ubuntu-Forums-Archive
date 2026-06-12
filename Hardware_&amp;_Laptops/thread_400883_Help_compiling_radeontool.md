---
title: "Help compiling radeontool?"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by Abdi110 on 2007-04-04
[http://fdd.com/software/radeon/](http://fdd.com/software/radeon/)

The versions off of that site have an option/switch called power (off/on). 1.5-3 off of the repos doesn't. I've spent a few hours searching the web trying to find some sort of general newb tutorial on how to compile stuff, but no dice. Anyone mind giving me a bit of direction on how to do this? Thanks.

---

### Post by teaker1s on 2007-04-05
You will need to install the essential build files to compile the driver:
 ```
sudo apt-get update
 sudo apt-get install build-essential
```

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)
 ```
sudo apt-get install linux-headers-`uname -r`
 sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build


```

Then
[http://www.tuxfiles.org/linuxhelp/softinstall.html]("http://www.tuxfiles.org/linuxhelp/softinstall.html")

---

### Post by Abdi110 on 2007-04-05
Thanks!

---

