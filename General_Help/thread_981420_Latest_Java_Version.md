---
title: "Latest Java Version"
date: 2008-11-13
forum: General Help
---

### Post by Ciwan on 2008-11-13
Hi Guys

Can someone please tell me how I can get the latest version of Java KDE for my Ubuntu OS.

I am using Eclipse to do my Java Programming, and some functions are not working, and I believe it is to do with my Java KDE being an old version.

Here is what I get, when I use the { java -version } command:

> *******@*******-Ubuntu:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)
*******@******-Ubuntu:~$

Any help, would be greatly appreciated.

Thanks

---

### Post by binbash on 2008-11-13
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

dont forget to 

sudo update-java-alternatives -l

list your java alternatives and select (sudo update-java-alternatives -s NAME) it 

PS : you may need to install sun-java6-jdk

---

### Post by Ciwan on 2008-11-13
Hi Binbash

> **binbash said:**
> PS : you may need to install sun-java6-jdk

That is what I wanted to do !!

Will the Sudo code you've provided do that for me ? **OR** would I need another sudo code to install the Java6-jdk ??

Thanks

---

