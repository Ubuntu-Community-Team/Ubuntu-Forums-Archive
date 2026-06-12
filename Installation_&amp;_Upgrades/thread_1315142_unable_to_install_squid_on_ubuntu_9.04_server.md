---
title: "unable to install squid on ubuntu 9.04 server"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by mady03sam on 2009-11-05
[SIZE=2]hi,
   im unable to install squid on ubuntu 9.04 im getting error like FAIL TO FETCH THE FILES,


root#sudo apt-get install squid

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  squid-common
Suggested packages:
  squidclient squid-cgi logcheck-database resolvconf
The following NEW packages will be installed:
  squid squid-common
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 1193kB of archives.
After this operation, 6857kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  squid-common squid
Authentication warning overridden.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main squid-common 2.7.STABLE3-4.1ubuntu1
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main squid 2.7.STABLE3-4.1ubuntu1
  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/squid/squid-common_2.7.STABLE3-4.1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/squid/squid-common_2.7.STABLE3-4.1ubuntu1_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.7.STABLE3-4.1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.7.STABLE3-4.1ubuntu1_i386.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


and i udated ma ubuntu but there too im getting fail to fetch i changed ma server for best server n im getting the same error 'failed to fetch and connection failed' can anyone tell what is the main issue im facing with, please resolve this and send me a quick reply.[/SIZE]

---

### Post by dvlchd3 on 2009-11-05
Are you connected to the Internet?  Can you ping google?

```

ping google.com

```

---

### Post by mady03sam on 2009-11-05
yes ma connection is perfect just now i checked ping google.com ..............

64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=1 ttl=52 time=220 ms
64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=2 ttl=52 time=218 ms
64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=3 ttl=52 time=225 ms
64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=4 ttl=52 time=220 ms
64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=5 ttl=52 time=220 ms
64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=6 ttl=52 time=218 ms
64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=7 ttl=52 time=222 ms

---

### Post by mady03sam on 2009-11-05
[dvlchd3]("http://ubuntuforums.org/member.php?u=295128") what happend to ma server please give reply n im new to dis ubuntu server

---

### Post by tsaowang on 2009-11-05
Hi,

Did you try this before ?

apt-get update -o Acquire::http::No-Cache=True

---

### Post by mady03sam on 2009-11-05
thanx for ur reply but i got dis............

:~$ sudo apt-get update -o Acquire::http::No-Cache=True 
 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  Connection failed
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  Connection failed
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mady03sam on 2009-11-05
do any1 know about this error please reply me im waiting for ur valuable reply....................
                                                                                                                                                Thanx in advance

---

### Post by dvlchd3 on 2009-11-05
That is extremely odd.  It looks like you cannot connect to the US repos.

Shoulda had you try to ping this first, sorry:

```

ping us.archive.ubuntu.com

```

If you can't, try a different repo ([https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors))

If you can ping the repository, try to use aptitude instead of apt-get.  It may be something screwy with apt-get

```

sudo aptitude update

```

If this still does not work, I'm out of ideas...hopefully someone else from the community will be able to help!

---

### Post by mady03sam on 2009-11-05
:~$ ping us.archive.ubuntu.com

PING us.archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=52 time=200 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=4 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=5 ttl=52 time=199 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=6 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=7 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=8 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=9 ttl=52 time=200 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=10 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=11 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=12 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=13 ttl=52 time=198 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=14 ttl=52 time=199 ms

it's gettin ping to us.archive but after dat im gettin d same error...................

:~$ sudo aptitude update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
  Connection failed
Reading package lists... Done

---

### Post by mady03sam on 2009-11-06
hey **dvlchd3** i resolved dis issue its jus to change or edit **http's** to **ftp's** in **gedit** **/etc/apt/source.list** .........and after dat go for [B]update
apt-get install update


[/B]

---

### Post by x.knight on 2009-12-11
dear please define your DNS in /etc/resolv.conf then you will be able to do so ping is the different thing

---

