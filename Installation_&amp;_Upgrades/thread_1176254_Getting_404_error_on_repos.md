---
title: "Getting 404 error on repos"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by jaxxstorm on 2009-06-02
Hello,

I've disabled all repos, then tried updating and still getting 404 error. Here is my current sources.list

```

#http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
#newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb-src http://ppa.launchpad.net/claws-mail/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/claws-mail/ppa/ubuntu jaunty main


```

As you can see I've removed all repos one by one and got nowhere, still get a 404. Anything else I can check?

---

### Post by Partyboi2 on 2009-06-02
Hi, can you open a terminal and post the output to
```
sudo apt-get update
```

---

### Post by jaxxstorm on 2009-06-02
> **Partyboi2 said:**
> Hi, can you open a terminal and post the output to
```
sudo apt-get update
```

```


Ign http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-en_GB
Ign http://archive.ubuntu.com jaunty Release
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty/main Packages
Err http://archive.ubuntu.com jaunty/main Packages
  404 Not Found
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

I can enable other repos if needed, but thought I'd enable one that I knew worked for testing purposes.

---

### Post by MichaelSammels on 2009-06-02
Try using this repo:

```
http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/
```

---

### Post by MichaelSammels on 2009-06-02
Basically, the file Packages doesn't exist, but Packages.bz2 and Packages.gz do.

---

### Post by jaxxstorm on 2009-06-02
> **MichaelSammels said:**
> Try using this repo:

```
http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/
```

I added it as 

```


deb http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/


```

and also tried

```

deb-src http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/

```

And it gave malformed line error?

Am I missing something?

---

### Post by jaxxstorm on 2009-06-02
I've just tried backing up sources.list and using [this one]("http://ubuntuforums.org/archive/index.php/t-997890.html") instead and still got errors

```

Ign http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-en_GB
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_GB
Ign http://archive.ubuntu.com jaunty/universe Translation-en_GB
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_GB
Ign http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com jaunty-security Release.gpg
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_GB
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_GB
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_GB
Ign http://archive.ubuntu.com jaunty Release        
Ign http://archive.ubuntu.com jaunty-updates Release
Ign http://archive.ubuntu.com jaunty-security Release
Ign http://archive.ubuntu.com jaunty/main Packages  
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/main Sources   
Ign http://archive.ubuntu.com jaunty/restricted Sources
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/universe Sources
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/multiverse Sources
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/main Sources
Ign http://archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Sources
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/main Sources
Ign http://archive.ubuntu.com jaunty-security/restricted Sources
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/universe Sources
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/main Sources
Ign http://archive.ubuntu.com jaunty/restricted Sources
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/universe Sources
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/multiverse Sources
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/main Sources
Ign http://archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Sources
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/main Sources
Ign http://archive.ubuntu.com jaunty-security/restricted Sources
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/universe Sources
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Sources
Err http://archive.ubuntu.com jaunty/main Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty/main Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty/restricted Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty/universe Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty/universe Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty/multiverse Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/main Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/main Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/restricted Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/universe Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/multiverse Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/main Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/main Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/restricted Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/universe Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/universe Sources
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/multiverse Sources
  404 Not Found
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
briggsl@leblt:~$ E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by MichaelSammels on 2009-06-02
Here are my repos:

```
Type: Binary
URI: http://archive.canonical.com/ubuntu
Distribution: jaunty
Components: partner
```

and this:

```
Type: Source
URI: http://archive.canonical.com/ubuntu
Distribution: jaunty
Components: partner
```

---

### Post by jaxxstorm on 2009-06-02
> **MichaelSammels said:**
> Here are my repos:

```
Type: Binary
URI: http://archive.canonical.com/ubuntu
Distribution: jaunty
Components: partner
```

and this:

```
Type: Source
URI: http://archive.canonical.com/ubuntu
Distribution: jaunty
Components: partner
```

Apologies, I may be being dim, but how am I supposed to use this? I've tried many different repos and it didn't help

---

### Post by MichaelSammels on 2009-06-02
System -> Administration -> Software Sources

Go to the third party software, you can edit/add repos.

---

### Post by jaxxstorm on 2009-06-02
> **MichaelSammels said:**
> System -> Administration -> Software Sources

Go to the third party software, you can edit/add repos.

Ah, sorry, should have made it clear. I don't run GNOME, I run OpenBox via Crunchbang Linux, so I can either use synaptic or manually edit.

I'd install the software sources manager, but I can't because I get 404 errors :(

---

### Post by MichaelSammels on 2009-06-02
Oh right. Try editing your sources.lst. Do a:

```
grep sources.list
```
if that finds nothing:
```
grep sources.lst
```

---

