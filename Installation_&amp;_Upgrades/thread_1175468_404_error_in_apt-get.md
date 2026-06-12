---
title: "404 error in apt-get"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by atomax27 on 2009-06-01
Hi,
 
I am trying to install Open SSH for a Ubuntu Gutsy 7.10; whenever I try apt-get install, it comes up with such error:
```
 
 
The following extra packages will be installed:
  openssh-client
Suggested packages:
  ssh-askpass xbase-clients libpam-ssh keychain rssh molly-guard
The following NEW packages will be installed:
  openssh-server
The following packages will be upgraded:
  openssh-client
1 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 904kB of archives.
After unpacking 655kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") gutsy-updates/main openssh-client 1:4.6p1-5ubun
tu0.1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") gutsy-updates/main openssh-server 1:4.6p1-5ubun
tu0.1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh)-
client_4.6p1-5ubuntu0.1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh)-
server_4.6p1-5ubuntu0.1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis
sing?

```
 
I have used the source list from the following thread:
 
[http://ubuntuforums.org/showthread.php?t=579729](http://ubuntuforums.org/showthread.php?t=579729)

---

### Post by mhgsys on 2009-06-01
I don't think 7.10 is still supported.

  Meaning repository's are no longer available on-line.

---

### Post by drs305 on 2009-06-01
The repositories for 7.10 are no longer officially supported. Here are the dates for the various versions:
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

 If you really don't want to upgrade, you can gain access to the old repositories by opening your sources.list and replacing the http address with the archived repository address. Of course, these archived repositories are available but are not updated.

Before doing this, make a backup copy of your current sources.list, then open the file for editing:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list

```

You should see lines like: 
deb **[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)** gutsy universe

Replace the highlighted portion of *all* the entries with:
deb **[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)** gutsy universe

---

