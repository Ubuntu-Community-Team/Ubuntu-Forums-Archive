---
title: "trouble installing JDownloader"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by alid1712 on 2009-06-01
I really need help on how to install JDownloader for my Ubuntu 9.04.
Can anyone help me?

I tried following this steps at  [http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/](http://pagesofinterest.net/blog/2009/05/installing-jdownloader-in-ubuntu/) but it failed[I].
[/I]

---

### Post by Mighty_Joe on 2009-06-01
Exactly what "failed"?  
I downloaded the Linux version and unzipped it into ~/bin directory.  I open a console, change to the ~/bin/JDownloader directory and invoke "java -jar JDownloader.jar".  You could also create a launcher to invoke the command, if that is easier for you.

---

### Post by alien-377h on 2009-10-25
I don't know if you've got the answer.


This worked for me

> **SCBrazil said:**
> HI,
This is an old thread by now but you never know, someone else may end up here looking how to install the best download manager there is.

The best way to install it is thus (I'm a Kubuntu user but I think the method is the same for Ubuntu);

1. From your package manager get 'Sun-Java6-jre' (this is the latest version as of today).

2. After it has installed open a Terminal, copy and paste;

wget [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh) && chmod +x jd.sh && ./jd.sh

The Terminal DL will end very quickly and then you'll get JDownloader's own window which will complete the process for you.

You're done.

---

