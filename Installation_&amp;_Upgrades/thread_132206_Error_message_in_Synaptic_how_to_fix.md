---
title: "Error message in Synaptic: how to fix?"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-17
When I open Synaptic, I get this error:

> 
 Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages)

Can someone advise on the procedure to correct this? Thanks.

---

### Post by Turtle.net on 2006-02-17
You should verify that there is no double entry in your file /etc/apt/sources.list
What you can do if there is no double entry is```
$sudo mv /etc/apt/sources.list /etc/apt/sources.list.back
$sudo touch /etc/apt/sources.list
$sudo apt-get update
$sudo mv /etc/apt/sources.list.back /etc/apt/sources.list
$sudo apt-get update
```
and launch Synaptic...

---

### Post by Coelocanth on 2006-02-17
Here's my /etc/apt/sources.list:

> 
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

Anything need to be changed there, or should I go ahead with the commands you suggested (thanks for the help, btw)?

---

### Post by Turtle.net on 2006-02-17
In fqct you have twice the same entry for multiverse ```

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe multiverse
 
 deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
 
 deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
 
 deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse
```
In fact ```
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe multiverse
``` is the same thing as ```
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse
```

So remove the line ```
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse
``` using ```
$sudo gedit /etc/apt/sources.list
``` and then ```
$sudo apt-get update
```
That should solve your problem ;)

---

### Post by Turtle.net on 2006-02-17
You can also have an interesting reading on this subject at
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
or
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Coelocanth on 2006-02-17
Many thanks! I was on the right track, but I didn't want to get too trigger happy with the editor without knowing for sure what I was doing. Appreciate the help and the links.

---

