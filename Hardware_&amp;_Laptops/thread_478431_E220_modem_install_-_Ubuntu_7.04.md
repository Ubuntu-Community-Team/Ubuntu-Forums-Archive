---
title: "E220 modem install - Ubuntu 7.04"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by johandutoit2000 on 2007-06-19
**I downloaded the new Vodafone Mobile Connect drivers at **

[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=7](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=7)

**The file I downloaded was **

vodafone-mobile-connect-card-driver-for-linux_0.9.6_all_feisty.deb

**When I run it in Ubuntu 7.04 (I am totally new to Linux, so I double click), I get the following error.**

"Dependancy is not satisfiable: python-twisted"

**My Kernel version during bootup is 2.6.20-15**
**By using Add Remove Apps, I can see that Python Interpreter 2.5 is installed.**

I have gone through these forums, but cannot find any help.

---

### Post by handaxe on 2007-06-19
Go to "System" -> "Administration" and then run "Synaptic Package Manager".

Search under "name" for python-twisted.  You will find what you need. Install via Synaptic.

HA

---

### Post by johandutoit2000 on 2007-06-20
I searched under "name". Got nothing. This is a fresh install of Ubuntu 7.04. What to try next?

---

### Post by handaxe on 2007-06-20
what happens if you try from a terminal:

```
sudo apt-get update
sudo apt-get install python-twisted
```??

HA

---

### Post by johandutoit2000 on 2007-07-01
**sudo apt-get update**

Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty Release.gpg
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates Release.gpg
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Translation-en_ZA
  Could not resolve 

'za.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_ZA
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_ZA
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_ZA
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_ZA
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_ZA
  Could not resolve 

'security.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/multiverse Translation-en_ZA
  Could not 

resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/universe Translation-en_ZA
  Could 

not resolve 'za.archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign 

[http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted 

Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-

security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign 

[http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-

security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Ign 

[http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main 

Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
 

 Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  Could not 

resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  Could not resolve 

'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 

'security.ubuntu.com'
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_ZA
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_ZA
Ign 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty Release
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates Release
Ign 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Packages
Ign 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Sources
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Sources
Ign 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Sources
Ign 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe 

Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-

updates/restricted Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Sources
Ign 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-

updates/multiverse Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/universe Packages
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Sources
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Sources
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Sources
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Sources
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Sources
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/multiverse Packages
  Could not resolve 'za.archive.ubuntu.com'
Err 

[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/universe Packages
  Could not resolve 'za.archive.ubuntu.com'
Failed to 

fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not resolve 'za.archive.ubuntu.com'
Failed 

to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_ZA.bz2)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_ZA.bz2)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-)

en_ZA.bz2  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-)

en_ZA.bz2  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2)  Could not 

resolve 'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-](http://za.archive.ubuntu.com/ubuntu/dists/feisty-)

updates/restricted/i18n/Translation-en_ZA.bz2  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_ZA.bz2)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-](http://za.archive.ubuntu.com/ubuntu/dists/feisty-)

updates/universe/i18n/Translation-en_ZA.bz2  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed 

to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_ZA.bz2)  Could not resolve 

'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-](http://security.ubuntu.com/ubuntu/dists/feisty-)

security/restricted/i18n/Translation-en_ZA.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2)  Could not resolve 

'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-](http://security.ubuntu.com/ubuntu/dists/feisty-)

security/multiverse/i18n/Translation-en_ZA.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2)  Could not resolve 

'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-)

i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  Could not resolve 

'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz) 

 Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-](http://security.ubuntu.com/ubuntu/dists/feisty-)

security/restricted/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Could not resolve 

'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-](http://security.ubuntu.com/ubuntu/dists/feisty-)

security/universe/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  Could not resolve 

'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-](http://security.ubuntu.com/ubuntu/dists/feisty-)

security/multiverse/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Could not resolve 

'security.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  

Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  

Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-)

i386/Packages.gz  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-](http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-)

i386/Packages.gz  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-](http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-)

i386/Packages.gz  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-)

i386/Packages.gz  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-](http://za.archive.ubuntu.com/ubuntu/dists/feisty-)

updates/main/source/Sources.gz  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  Could not resolve 

'za.archive.ubuntu.com'
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-)

i386/Packages.gz  Could not resolve 'za.archive.ubuntu.com'
Failed to fetch 

[http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  Could not resolve 

'za.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, 

or old ones used instead.



**sudo apt-get install python-twisted**

johan@johan-laptop:~$ sudo apt-get install python-twisted
Reading package lists... Done
Building 

dependency tree       
Reading state information... Done
E: Couldn't find package python-twisted

---

### Post by Sybrand on 2007-09-22
Hi,

I just want to know if you had any luck installing python-twisted yet? Having the same problem.

Regards

Sybrand

---

### Post by johandutoit2000 on 2007-09-23
No, I gave up on ubuntu. They want the whole world to embrace open source, but the hurdles are just too big. I am sticking with what works.

---

