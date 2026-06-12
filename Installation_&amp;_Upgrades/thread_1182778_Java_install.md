---
title: "Java install"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by winyve on 2009-06-09
Hello guys

I'm totally new with ubuntu and want to learn it..
But my problem is I don't even know how to install a simple program.. 
I downloaded java here ([http://www.java.com/nl/download/linux_manual.jsp?locale=nl&host=www.java.com:80](http://www.java.com/nl/download/linux_manual.jsp?locale=nl&host=www.java.com:80)) and downloaded the first 1.
I tried with terminal but cant get it :(

thanks

---

### Post by PmDematagoda on 2009-06-09
> **winyve said:**
> Hello guys

I'm totally new with ubuntu and want to learn it..
But my problem is I don't even know how to install a simple program.. 
I downloaded java here ([http://www.java.com/nl/download/linux_manual.jsp?locale=nl&host=www.java.com:80](http://www.java.com/nl/download/linux_manual.jsp?locale=nl&host=www.java.com:80)) and downloaded the first 1.
I tried with terminal but cant get it :(

thanks

You don't need to go through that to install Java, you can simply open up the Synaptic Package Manager in System->Administration, search for either:-

1) openjdk, which is the open source version of Java, which should replace the normal Java plugin in the future.

2) sun-java6, which is the proprietary version of Java, which you probably get from the Java website, but OpenJDK is still very much useful and it is as good as it's proprietary counter-part though it does have a few problems here and there.

and, depending on what you want, install the required packages.

Edit:- On Ubuntu, programs are usually installed with the use of online repositories, you can use these repositories with either Add/Remove Programs or the Synaptic Package Manager in order to manage the applications you have installed on your system. Manually downloading and installing programs are not really required except in some rare cases.

---

### Post by winyve on 2009-06-09
Ok thank you..
Could I install every program like that?

---

### Post by PmDematagoda on 2009-06-09
> **winyve said:**
> Ok thank you..
Could I install every program like that?

If it is in the repositories, then yes. :)

---

