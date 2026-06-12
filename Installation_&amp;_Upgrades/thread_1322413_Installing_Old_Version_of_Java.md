---
title: "Installing Old Version of Java"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Wyphy on 2009-11-10
I'm trying to install an old version of Java because I have a program that doesn't run correctly on new ones; no idea why.

I'm pretty much a newb, so specific directions or links are appreciated.
Using Jaunty, trying to install Java JRE 6.0 (jre-6-linux-amd64.bin, DL directly from Sun's site)
I uninstalled the current version of JRE.

I did some searches and found:
[http://ubuntuforums.org/showthread.php?t=211104](http://ubuntuforums.org/showthread.php?t=211104)
which has a pointer to:
[http://www.debian-administration.org/articles/142](http://www.debian-administration.org/articles/142)

I followed the directions of the second link but when I run the make-jpkg and I get this message:
> Creating temporary directory: /tmp/make-jpkg.TZZyvVUWuB
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: amd64
Detected Debian GNU type: x86_64-linux-gnu

No matching plugin was found.
Removing temporary directory: doneGot some ideas?
Thanks.

---

### Post by kkkkdddd on 2009-11-11
Installing of old version of Java 6 is a bad idea because:
-it is probably not going to solve your problem
-it will make your system vulnerable

You should rather install the newest version of Java 5. 

```
sudo apt-get install sun-java5-jre
```

Or
[https://dct.sun.com/dct/forms/reg_us_0211_979_0.jsp](https://dct.sun.com/dct/forms/reg_us_0211_979_0.jsp)

---

