---
title: "Issues with Lenovo Y500"
date: 2014-07-18
forum: Hardware
---

### Post by jopi2 on 2014-07-18
I am getting the following error message with Ubuntu 12.04.1 LTS x64, 14.04 LTS x64 and also with Zorin OS 9 X64:

[https://www.dropbox.com/s/cd9fbpd2cz16ams/2014-07-18%2014.03.19.jpg](https://www.dropbox.com/s/cd9fbpd2cz16ams/2014-07-18%2014.03.19.jpg)

12.04 LTS was installed earlier and everything worked fine until some upgrades that were installed last tuesday. After that the OS just stopped working outputting only the error message shown above. Even a clean install won't help so I am guessing it's related to some updates that are also downloaded during installation. 

Any ideas how to get everything to work again?

---

### Post by WinEunuchs2Unix on 2014-07-19
Boot with the Live DVD and check the disk for errors.  Check the Kernel log file for error messages using "sudo gedit /var/log/kern.log".

---

### Post by jopi2 on 2014-07-21
I attached kernel log file to this post. Hopefully somebody can help me with this issue.

---

