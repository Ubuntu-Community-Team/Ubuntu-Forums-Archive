---
title: "Apt problems - missing packages"
date: 2005-11-26
forum: General Help
---

### Post by stocksy on 2005-11-26
I have a PIII Toshiba laptop running Breezy, which seems to have lost track of available packages, e.g:

[FONT="Courier New"]stocksy@mail2:~$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree... Done
Package postfix is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package postfix has no installation candidate[/FONT]

I've checked and double checked my /etc/apt/sources.list against my work PC (also running Breezy) and I can't see anything wrong:

[FONT="Courier New"]deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse[/FONT]

I've run 'apt-get check' which returns no problems, using the '-f' option with apt-get, 'apt-get clean'... don't really know what else to try.  Any suggestions would be gratefully received.

---

### Post by oskude on 2005-11-26
your maybe missing "sudo apt-get update", or
its named something else, try "apt-cache search postfix"

---

### Post by stocksy on 2005-11-26
[QUOTE=oskude]your maybe missing "sudo apt-get update", or
its named something else, try "apt-cache search postfix"[/QUOTE]
sudo apt-get update runs OK.  apt-cache search postfix returns no output.

---

### Post by oskude on 2005-11-26
[QUOTE=stocksy]sudo apt-get update runs OK.  apt-cache search postfix returns no output.[/QUOTE]thats odd, here works```
hacker@testlab:~$ apt-cache show postfix
Package: postfix
Priority: optional
Section: mail
Installed-Size: 2140
Maintainer: LaMont Jones <lamont@debian.org>
Architecture: i386
Version: 2.2.4-1ubuntu2
Replaces: postfix-doc (<< 1.1.7-0), postfix-tls
Provides: mail-transport-agent, postfix-tls
Depends: libc6 (>= 2.3.4-1), libdb4.2, libsasl2 (>= 2.1.19), libssl0.9.7, debconf (>= 0.5) | debconf-2.0, netbase, adduser (>= 3.48), dpkg (>= 1.8.3), lsb-base (>= 1.3-9ubuntu3)
Recommends: mail-reader, resolvconf
Suggests: procmail, postfix-mysql, postfix-pgsql, postfix-ldap, postfix-pcre
Conflicts: mail-transport-agent, smail, libnss-db (<< 2.2-3), postfix-tls
Filename: pool/main/p/postfix/postfix_2.2.4-1ubuntu2_i386.deb
Size: 910878
MD5sum: 4b6c5c034d750e894d6f198e6c2f2256
Description: A high-performance mail transport agent
 Postfix is Wietse Venema's mail transport agent that started life as an
 alternative to the widely-used Sendmail program.  Postfix attempts to
 be fast, easy to administer, and secure, while at the same time being
 sendmail compatible enough to not upset existing users. Thus, the outside
 has a sendmail-ish flavor, but the inside is completely different.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```and "sudo apt-get install postfix" worked too, hmm...

edit: can you "apt-get install" anything ?

---

### Post by stocksy on 2005-11-26
> edit: can you "apt-get install" anything ?

I can install the few things I can find with apt-cache search:

```

stocksy@mail2:~$ sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Hit http://archive.ubuntu.com breezy Release    
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/universe Packages
Hit http://archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Fetched 20.0kB in 0s (27.6kB/s)
Reading package lists... Done


stocksy@mail2:~$ sudo apt-get install curl
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 153kB of archives.
After unpacking 250kB of additional disk space will be used.
Get:1 http://security.ubuntu.com breezy-security/main curl 7.14.0-2ubuntu1.1 [153kB]
Fetched 153kB in 1s (151kB/s)
Selecting previously deselected package curl.
(Reading database ... 71016 files and directories currently installed.)
Unpacking curl (from .../curl_7.14.0-2ubuntu1.1_i386.deb) ...
Setting up curl (7.14.0-2ubuntu1.1) ...
stocksy@mail2:~$ 

```

---

### Post by oskude on 2005-11-26
this is very odd, or we have forgotten something very obvious :)
i hope some one with more experience with this could come up with something...

edit:
i allso tried with your sources.list, works.... hmm :-k

---

### Post by stocksy on 2005-11-27
OK, I noticed that about every 3rd time, sudo apt-get update would fail to retrieve at least one file from archive.ubuntu.com.  I looked for a mirror of archive.ubuntu.com, but in doing so, found that *.archive.ubuntu.com resolves to the same two IPs.  Setting sources.list to get the packages from smellypoo.archive.ubuntu.com seems to fix it:

```

stocksy@mail2:~$ sudo apt-get update
...
stocksy@mail2:~$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre
Recommended packages:
  resolvconf
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 911kB of archives.
After unpacking 2191kB of additional disk space will be used.
Get:1 http://smellypoo.archive.ubuntu.com breezy/main postfix 2.2.4-1ubuntu2 [911kB]
Fetched 287kB in 1s (218kB/s) 
...

```

In fact, it now works if I set it back to archive.ubuntu.com too! :???: Strange, but what the heck, it works!

```

stocksy@mail2:~$ sudo apt-get update
...
stocksy@mail2:~$ sudo apt-get install stress
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  stress
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.6kB of archives.
After unpacking 94.2kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/universe stress 0.18.4-1 [18.6kB]
Fetched 18.6kB in 0s (65.9kB/s)
...

```

Thanks for your efforts oskude :smile:

---

