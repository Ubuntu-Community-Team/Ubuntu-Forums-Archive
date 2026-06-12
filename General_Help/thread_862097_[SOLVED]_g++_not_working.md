---
title: "[SOLVED] g++ not working"
date: 2008-07-17
forum: General Help
---

### Post by The Midnight Coder on 2008-07-17
g++ wont work and I got this error when I ran sudo apt-get after fixing dpkg

> 
dpkg: serious warning: files list file for package `g++' missing, assuming package has no files currently installed.


---

### Post by The Midnight Coder on 2008-07-17
Anybody?

---

### Post by Archimedes0212 on 2008-07-17
have you tried removing it completely and reinstalling

  sudo apt-get remove g++

  sudo apt-get install g++

I forgot which program I messed up once, but i deleted files to it and my fix was to do something along these lines

---

### Post by The Midnight Coder on 2008-07-17
I had removed it earlier after that error and tried the exact same thing

It threw up this:
> 
fabian23@fabian23-desktop:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  g++-multilib
The following NEW packages will be installed:
  g++
0 upgraded, 1 newly installed, 0 to remove and 166 not upgraded.
Need to get 0B/1440B of archives.
After this operation, 41.0kB of additional disk space will be used.
(Reading database ... 96142 files and directories currently installed.)
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/g++_4%3a4.2.3-1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/bin/i486-linux-gnu-g++', which is also in package gcc
Errors were encountered while processing:
 /var/cache/apt/archives/g++_4%3a4.2.3-1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
fabian23@fabian23-desktop:~$ 


---

### Post by Archimedes0212 on 2008-07-17
hmmmm.  Did you say earlier that there was a problem with dpkg that you fixed?  If so, what was it?

---

### Post by The Midnight Coder on 2008-07-17
Posted it earlier: [http://ubuntuforums.org/showthread.php?t=861128](http://ubuntuforums.org/showthread.php?t=861128)

---

### Post by The Midnight Coder on 2008-07-20
Anybody have any clue on how to get g++ back?

---

### Post by cdtech on 2008-07-20
You may need to purge ::.
sudo apt-get remove --purge g++

---

### Post by The Midnight Coder on 2008-07-20
> 
fabian23@fabian23-desktop:~$ sudo apt-get remove --purge g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package g++ is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 166 not upgraded.
fabian23@fabian23-desktop:~$


Tried installing again and:

> 
fabian23@fabian23-desktop:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  g++-multilib
The following NEW packages will be installed:
  g++
0 upgraded, 1 newly installed, 0 to remove and 166 not upgraded.
Need to get 0B/1440B of archives.
After this operation, 41.0kB of additional disk space will be used.

(Reading database ... 96691 files and directories currently installed.)
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/g++_4%3a4.2.3-1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/bin/i486-linux-gnu-g++', which is also in package gcc
Errors were encountered while processing:
 /var/cache/apt/archives/g++_4%3a4.2.3-1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
fabian23@fabian23-desktop:~$ 


What now?

---

### Post by The Midnight Coder on 2008-07-21
bump

anybody?

---

### Post by The Midnight Coder on 2008-07-24
do you mean to tell me that nobody here knows how to fix this?

---

### Post by Potatoj316 on 2008-07-24
Yeah, I know how to fix this one!!! (celebration over)

install the package build-essential
```
sudo aptitude install build-essential
```

if this dosent work disregard the celebration at the beginning

---

### Post by The Midnight Coder on 2008-07-24
Taken from the output:

> 
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/g++_4%3a4.2.3-1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/bin/i486-linux-gnu-g++', which is also in package gcc


> 
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/g++_4%3a4.2.3-1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:



> 
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.1.1); however:
  Package g++ is not installed.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Errors were encountered while processing:
 build-essential


---

### Post by Potatoj316 on 2008-07-24
Did you use aptitude (not apt-get)?  If not then you should try it, it might make it work.

---

### Post by jimv on 2008-07-24
Go download the deb file for g++ and then run this command:

sudo dpkg --force-all -i whateveryourpackageiscalled

EDIT:

Here's the download link:
[http://packages.ubuntu.com/hardy/g++](http://packages.ubuntu.com/hardy/g++)

---

### Post by The Midnight Coder on 2008-07-24
Thanks jimv. It works now

@Potatoj316: to clear things up....i did use aptitude

---

