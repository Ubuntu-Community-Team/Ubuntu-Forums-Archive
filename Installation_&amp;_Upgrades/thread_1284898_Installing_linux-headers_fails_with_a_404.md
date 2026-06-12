---
title: "Installing linux-headers fails with a 404"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by vanderkerkoff on 2009-10-07
Hello.

Im running Hardy Server

2.6.24-24-server #1 SMP Wed Apr 15 15:41:09 UTC 2009 x86_64 GNU/Linux

I need to install the linux-headers for that kernel so that I can install the VMware tools.

When I run this command

sudo aptitude install linux-headers-`uname -r`

I'm getting this error back

Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-24 2.6.24-24.55
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-24 2.6.24-24.55
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-24-server 2.6.24-24.55
  404 Not Found
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.24-24_2.6.24-24.55_all.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.24-24_2.6.24-24.55_all.deb:) 404 Not Found

Anyone got any ideas how to resolve this or is this a temporary glitch in the Ubuntu system?

Any help, greatly appreciated.

---

### Post by Partyboi2 on 2009-10-07
Hi, try changing your download server to another one in Software Sources under the 1st tab.

---

### Post by vanderkerkoff on 2009-10-07
Hi Partyboi2

You don't know how you'd do that from the command line do you?

I seem to remember something about /etc/apt/sources.list but can't remember the command to update that list.

Googling now, I'll post the solution back up here if I find it before you

---

### Post by vanderkerkoff on 2009-10-07
sudo aptitude update

not so hard :-)

---

### Post by oldos2er on 2009-10-07
There's some help, and a link to a list of mirror repositories here: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

