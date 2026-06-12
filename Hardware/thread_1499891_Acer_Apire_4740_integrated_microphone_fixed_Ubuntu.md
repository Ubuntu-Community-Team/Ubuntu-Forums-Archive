---
title: "Acer Apire 4740 integrated microphone fixed Ubuntu Lucid Lynx 10.04"
date: 2010-06-02
forum: Hardware
---

### Post by oscarperez on 2010-06-02
I recently bought and Acer Aspire 4740 laptop, but integrated microphone wasn't working.

The solution was Update ALSA from version 1.0.21 to 1.0.23

Here are the instructions:

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

         If you get this error when you are executing the following command:
 ```
$ sudo /etc/init.d/alsa-utils stop
sudo: /etc/init.d/alsa-utils: command not found
```
 then try:
```
$ sudo /sbin/alsa-utils stop 
```
 Thank you for the post this solved Acer Apire 4740 integrated  microphone problem on Ubuntu Lucid Lynx 10.04

---

