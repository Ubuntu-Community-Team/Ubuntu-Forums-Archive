---
title: "apt-get.real: not found"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by nikeshshk on 2009-05-23
apt-get install wget

[B]apt-get: install wget
/usr/bin/apt-get: 105: apt-get.real: not found
[/B]
somehow apt got removed can it be fixed?

---

### Post by Kevbert on 2009-05-23
Welcome to Ubuntu.
What do you get in Applications-Accessories-Terminal when you enter
```
sudo apt-get install -f
```
? You should get an error (something like apt-get command not found).
If you're sure that you've lost the apt package you can get it from [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/jaunty/apt") assuming that you're using Jaunty 9.04. Select the architecture by clicking on it, AMD64 for 64 bit or i386 for 32 bit PCs, select a server near you and select 'Open with (default)'. Enter your login password when prompted. You'll need to reboot the PC for changes to take effect.

---

### Post by nikeshshk on 2009-05-23
sorry kevbert I forgot to mention my ubuntu version.
I am using ubuntu 7.10
when i run this command
dpkg -i apt_0.7.20.2ubuntu6_i386.deb
it returned
dpkg-deb: --control apt_0.7.20.2ubuntu6_i386.deb /var/lib/dpkg/tmp.ci
/usr/bin/dpkg-deb: 52: /usr/lib/ia32-libs-tools/mangle: not found
dpkg: error processing apt_0.7.20.2ubuntu6_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 127
Errors were encountered while processing:
 apt_0.7.20.2ubuntu6_i386.deb

:(

---

### Post by Kevbert on 2009-05-23
Apt is installed in Ubuntu by default. Did you get any errors with the command I suggested ? This will also find and try to force a repair on any broken packages. The error suggests that the problem is with the dpkg-deb file.  It also seems that your apt package is out of date for Gutsy (should be 0.7.6).
It may also be worth installing the latest version of Ubuntu Jaunty Jackalope (9.04) as there are one or two security issues with Gutsy Gibbon (7.10).

---

### Post by nikeshshk on 2009-05-24
Thanks Kevbert for nice support
I reinstalled ubuntu gutsy ribbon (7.10) again.
I am not using a new jaunty version yet because if I use new 9.04 version I need to replace my whole hardware. I think 7.10 will not give lots of problem to me.
I will tell you how my apt got removed.
I added this line on my /etc/apt/sources.list

[B]deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) lenny main

[/B]and when I performed this
sudo apt-get install libcache-memcached-perl
my apt, aptitude and some others also got removed.

---

### Post by Kevbert on 2009-05-24
> **nikeshshk said:**
> Thanks Kevbert for nice support
I reinstalled ubuntu gutsy ribbon (7.10) again.
I am not using a new jaunty version yet because if I use new 9.04 version I need to replace my whole hardware. I think 7.10 will not give lots of problem to me.
I will tell you how my apt got removed.
I added this line on my /etc/apt/sources.list

[B]deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) lenny main

[/B]and when I performed this
sudo apt-get install libcache-memcached-perl
my apt, aptitude and some others also got removed.

Gutsy was my first working Linux operating system and it was very reliable. This why I moved over to Ubuntu, as my main OS, from Windows (I still use XP occassionally).  You should not mix different versions of Linux in your sources.list (even though Ubuntu is based on Debian).  What hardware do you have ? I've even installed 9.04 on a very old Athlon 900MHz and it runs fine (but a little slow) with an old Voodoo Banshee display card. The only minor problem is that the OS complains that the BIOS is a little old!

---

