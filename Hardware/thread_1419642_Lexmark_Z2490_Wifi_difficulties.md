---
title: "Lexmark Z2490 Wifi difficulties"
date: 2010-03-02
forum: Hardware
---

### Post by Syrrus24 on 2010-03-02
Suprisingly I found a driver for Linux on the Lexmark site for my printer, downloaded it, and after some trouble got to the installation of the driver. The only problem I have is with the root password of my computer. I've tried both my username password and the root password and still it will not accept it. It is 3 letters long though.

I would love to jump in the installation and mess with code to do all this but don't know how, if anyone has a better suggestion I'd be up for it. I'm running Ubuntu 9.1 and the driver is for red hat. (I'm a Linux n00b converting from Windows)

---

### Post by gitfiddler on 2010-03-11
Syrrus24,

I had the same problem, and I've just solved it. 

I have the Lexmark Prospect205. I successfully installed the printer software on a desktop machine running 8.04, but ran into the password problem on my laptop running 9.10. I found several threads about this problem, some of them labelled "Solved", but without details of the solution!

The Lexmark installer is looking for a "root" password and not your user password. Chances are, you don't have a password set for root.

I clicked on "System->Administration->Users and Groups". I clicked where it said "Click to Make Changes" and entered my *user* password. That brought up a form that allowed me to set a *root* password. I re-ran the shell script (lexmark-inkjet-09-driver-1.0-1.i386.deb.sh), entered my new *root* password and viola! it worked.

Incidentally, you mentioned that you are trying to run the Redhat driver. I think you'll have better luck with the Debian installer.

I hope this helps.

gitfiddler

---

### Post by gitfiddler on 2010-03-11
I just realized that I skipped a detail.

After entering my *user* password, I highlighted the "root" entry, then clicked on "Properties". *Then* the Properties form appeared, and I could set a password for root.

gitfiddler

PS. Wow, do I have to update my signature :roll:

---

### Post by w2vy on 2010-05-07
> **Syrrus24 said:**
> Suprisingly I found a driver for Linux on the Lexmark site for my printer, downloaded it, and after some trouble got to the installation of the driver. The only problem I have is with the root password of my computer. I've tried both my username password and the root password and still it will not accept it. It is 3 letters long though.

I would love to jump in the installation and mess with code to do all this but don't know how, if anyone has a better suggestion I'd be up for it. I'm running Ubuntu 9.1 and the driver is for red hat. (I'm a Linux n00b converting from Windows)

[http://www.downloaddelivery.com/downloads/pssd/drivers-linux-glibc2-x86.tar.gz]("http://www.downloaddelivery.com/downloads/pssd/drivers-linux-glibc2-x86.tar.gz")

This is the link I found on their site...

I am hoping this will also work for the Z2410 that I have..

Are these the RPM's you installed?

> 
tom@w2vy:~/Desktop/Lexmark_Z2490/drivers-linux-glibc2-x86$ ls -l
total 4128
-rw-r--r-- 1 tom tom  145735 2003-01-30 22:49 drivers-MVfonts-4.7.2-1.i386.rpm
-rw-r--r-- 1 tom tom 4070766 2003-01-30 22:50 drivers-MVprint-4.7.2-1.i386.rpm
tom@w2vy:~/Desktop/Lexmark_Z2490/drivers-linux-glibc2-x86$


tom

---

