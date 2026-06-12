---
title: "MySQL dependency problem after upgrading to KDE 4.3"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by hkb on 2009-08-16
After upgrading my KDE to 4.3 i started to get problems with my MySQL server and i cannot install new packages. I can upgrade but only if i force it. When i upgrade or install i get the following output:

```

_@_-desktop:~$ sudo apt-get -f install -V
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
   mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2)
Suggested packages:
   tinyca (0.7.5-2)
   mailx (20081101-2ubuntu1)
The following NEW packages will be installed:
   mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2)
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
46 not fully installed or removed.
Need to get 0B/23,6MB of archives.
After this operation, 79,4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 193883 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have Kubuntu 9.04.

Is there anyway to fix this so i can use my MySQL server again og use my system.

---

### Post by rungss on 2009-08-25
Have a look at the Thread..
[http://ubuntuforums.org/showthread.php?p=7830540](http://ubuntuforums.org/showthread.php?p=7830540)

I too have been having this problem...

I guess KDE requires mysql-server-5.0

If you have mysql-server-5.1 it asks to remove mysql-server-5.1 and install mysql-server-5.0

And when doing so it causes an error..

```

                         
The following NEW packages will be installed:  
  mysql-server-5.0                             
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.                             
Need to get 0B/23.6MB of archives.                            
After this operation, 79.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y                                   
Preconfiguring packages ...                                        
(Reading database ... 246874 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
**Aborting downgrade from (at least) 5.1 to 5.0.**
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by criley on 2009-09-04
Greetings,

I found that /var/lib/mysql existed (despite the fact that no mysql-server of any version was installed.)

I checked using lsof and found that no processes were using files in it.
rm -rf /var/lib/mysql fixed it for me and I was able to install mysql-server-5.0 after that.

---

### Post by rungss on 2009-09-04
> **criley said:**
> Greetings,

I found that /var/lib/mysql existed (despite the fact that no mysql-server of any version was installed.)

I checked using lsof and found that no processes were using files in it.
rm -rf /var/lib/mysql fixed it for me and I was able to install mysql-server-5.0 after that.

But...
That would remove all your Data with the Databases and Tables for your previous installation.

I couldn't afford to do that...

I was not sure if just copy pasting the same will work...

---

