---
title: "FTDI (FT2232) works under root only and not under normal user"
date: 2008-07-18
forum: General Help
---

### Post by alxlabs on 2008-07-18
Don't know if this is the right subforum to ask...

So, Ubuntu 8.04, kernel 2.6.24-16

I'm trying to port Win application working with custom device thru FTDI2232 USB controller using FTDI drivers & library ( [http://www.ftdichip.com/Drivers/D2XX.htm](http://www.ftdichip.com/Drivers/D2XX.htm) ) ver. 0.4.13

I can get device to work under root, and cannot under normal user. As per my understanding - problem is that lib is trying to access something in /dev/blahblah and permissions are not set properly...however I don't know how to find out which one it is trying to access. Any ideas how to figure that out?

---

### Post by alxlabs on 2008-08-25
Just for statistics or for somebody else trapped into the same thing....

After wrestling for a bit I gave up and used a workaround - I wrote small service which accesses FTDI chip and runs at system startup as root then creates a pipe (I used this as an example - [http://www.linuxhq.com/guides/LPG/node18.html](http://www.linuxhq.com/guides/LPG/node18.html) ). User application uses the pipe to comm. to service which comm. to FTDI and back thru another pipe...

---

