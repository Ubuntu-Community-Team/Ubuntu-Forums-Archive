---
title: "How do I install Cheese"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by jeff_flynn on 2009-04-27
I'm trying to install Cheese because using Gyachi my Microsoft Lifecam 1000 is bad quality. it says I need this: [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb)

jeff@jeff-desktop:~$ apt-get install cheese
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jeff@jeff-desktop:~$ sudo apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cheese
0 upgraded, 1 newly installed, 0 to remove and 154 not upgraded.
Need to get 685kB of archives.
After unpacking, 1114kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  cheese
Install these packages without verification [y/N]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe cheese 0.2.3-0ubuntu1
  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb) 404 Not Found [IP: 91.189.88.140 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

---

### Post by dox_drum on 2009-04-27
Go to **Applications --> Add/Remove**

and in the search tab look up for **cheese**

Finally apply the changes.

Edit: Perhaps if you use the Main repository instead of the local you are using it'll work.

---

### Post by ninjapirate89 on 2009-04-27
> **jeff_flynn said:**
> I'm trying to install Cheese because using Gyachi my Microsoft Lifecam 1000 is bad quality. it says I need this: [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb)

jeff@jeff-desktop:~$ apt-get install cheese
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jeff@jeff-desktop:~$ sudo apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cheese
0 upgraded, 1 newly installed, 0 to remove and 154 not upgraded.
Need to get 685kB of archives.
After unpacking, 1114kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  cheese
Install these packages without verification [y/N]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe cheese 0.2.3-0ubuntu1
  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb) 404 Not Found [IP: 91.189.88.140 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

Try 
```

sudo apt-get install cheese

```
or just find it in Add/Remove Programs.

Edit-> Beat to it.

---

### Post by jeff_flynn on 2009-04-27
it says it can't find [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb)

---

### Post by jeff_flynn on 2009-04-27
jeff@jeff-desktop:~$ sudo apt-get install cheese
[sudo] password for jeff:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jeff@jeff-desktop:~$

---

### Post by _Purple_ on 2009-04-27
Is your Synaptic Package Manager open when you are installing cheese? If so, close Synaptic Package Manager and then run this command.

---

### Post by jeff_flynn on 2009-04-27
> **_Purple_ said:**
> Is your Synaptic Package Manager open when you are installing chess? If so, close Synaptic Package Manager and then run this command.

I marked Cheese for installation in Synaptic Package Manager. This came up.

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cheese/cheese_0.2.3-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.140 80]

I tried in Terminal. This came up.

jeff@jeff-desktop:~$ sudo apt-get install cheese
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by _Purple_ on 2009-04-27
May be the server is down. In Synaptic Package Manager, go to Settings > Repositories and try to select different server and see if it works.

---

### Post by jeff_flynn on 2009-04-27
> **_Purple_ said:**
> May be the server is down. In Synaptic Package Manager, go to Settings > Repositories and try to select different server and see if it works.

I was using Canada Server, I switched to Main Server, then hit Reload, this came up:

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.140 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.140 80]

Edit: I tried Best Server, which was   [http://ubuntu.media.mit.edu/ubuntu](http://ubuntu.media.mit.edu/ubuntu).. and this came up:

[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/main/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/main/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/universe/source/Sources.gz:](http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found

---

