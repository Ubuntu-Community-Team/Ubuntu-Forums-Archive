---
title: "Software centre can't progress beyond 5%"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Shalafi76 on 2009-10-31
I have just installed Karmic on my laptop and I'm very happy with it.  Unfortunately the Software Center cannot progress beyond 5% when I try and install any software.  The program doesn't hang, it just can't progress.  Eventually it tells me to check my internet connection, which works well.

Any ideas??

PS: Karmic finally made my wireless work without delving deep into mad-wifi! Yay!

---

### Post by Sensiva on 2009-10-31
Try issuing the command 
```
sudo apt-get install <package name>
```And see what it gives you, I am sure it would say alot :D

---

### Post by Shalafi76 on 2009-11-03
Thanks Sensiva.

I tried it with the following results(abridged to avoid repitition):

After this operation, 2,220kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe libyaml-0-1 0.1.2-1
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/liby/libyaml/libyaml-0-1_0.1.2-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/liby/libyaml/libyaml-0-1_0.1.2-1_i386.deb)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

The software center eventually produces an error window informing me that it hasn't downloaded the package files and to check my internet connection, which I am using to post this, so it obviously works.

The repository has always worked with previous versions of Ubuntu.

Thanks again.

---

### Post by Sensiva on 2009-11-03
I checked this mirror and it worked for me, for various reasons it might not work for you, try changing this mirror to something else 
System > Administration > Software Sources
in the **Download from **field chose another mirror and check again

Since your Ubuntu cannot reach this mirror, I guess you need many updates. Please after changing the mirror update your system using Update Manager

Good Luck

---

### Post by Shalafi76 on 2009-11-03
Success!!  Ah, it tastes so sweet! :D

I changed my software source from the Australian one to the main server, performed some updates and it works.

Thank you for your help Sensiva, you suggestion worked well.

Cheers.

---

### Post by Sensiva on 2009-11-03
> **Shalafi76 said:**
> Success!!  Ah, it tastes so sweet! :D

I changed my software source from the Australian one to the main server, performed some updates and it works.

Thank you for your help Sensiva, you suggestion worked well.

Cheers.

You are most welcome, wish me luck getting my Karmic up soon ;)

And don't forget to mark this thread as solved

---

