---
title: "can't download python2.5-dev and/or python-dev"
date: 2008-07-21
forum: General Help
---

### Post by myidbe on 2008-07-21
Hello,

I'm interested in contributing (ever so humbly) to wesnoth.org and so went about trying to compile the actual development/svn version. The list of required libraries is [here]("http://www.wesnoth.org/wiki/CompilingWesnoth").

python-dev is included on that list, but I get a funny error message from synaptic/apt when I try to download it:

Synaptic gives:
```
python-dev:
 Depends: python2.5-dev but it is not going to be installed
```

From the command line, "sudo apt-get install python-dev" gives:

```
malcolm@malcolm-laptop:~$ sudo apt-get install python-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-dev: Depends: python2.5-dev (>= 2.5.2) but it is not going to be installed
E: Broken packages

```

I currently have python (2.5.2-0ubuntu1) installed (which depends on python2.5, etc.), and am running hardy heron. Any help would be greatly appreciated :confused:

---

### Post by ibutho on 2008-07-21
Have you tried updating your package sources first?

---

### Post by dracayr on 2008-07-21
try using aptitude: ```
sudo aptitude install python-dev
```

dracayr

---

### Post by myidbe on 2008-07-22
The output from "sudo aptitude python-dev" is as follows:

```
malcolm@malcolm-laptop:~$ sudo aptitude install python-dev
[sudo] password for malcolm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  python2.5-dev 
The following packages are unused and will be REMOVED:
  libdns32 linux-headers-2.6.24-16 linux-headers-2.6.24-16-generic o3read 
The following packages have been automatically kept back:
  firefox-2 
The following NEW packages will be installed:
  python-dev 
0 packages upgraded, 2 newly installed, 4 to remove and 1 not upgraded.
Need to get 1887kB of archives. After unpacking 64.1MB will be freed.
The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
python2.5 [2.5.2-2ubuntu5 (now) -> 2.5.2-2ubuntu4 (hardy)]
python2.5-minimal [2.5.2-2ubuntu5 (now) -> 2.5.2-2ubuntu4 (hardy)]

Score is 114

Accept this solution? [Y/n/q/?] 

```

Ok, so I said yes to that, and everything worked out. I'm still confused as to why all this happened though: also, why is it quoting firefox-2 in the output above? 

My package sources are below:

```
malcolm@malcolm-laptop:~$ cat /etc/apt/sources.list
## MAIN
deb http://ch.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://ch.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

## PROPOSED REPOSITORY
deb http://ch.archive.ubuntu.com/ubuntu hardy-proposed restricted main multiverse universe
deb-src http://ch.archive.ubuntu.com/ubuntu hardy-proposed restricted main multiverse universe

## BACKPORTS REPOSITORY

## SQUEAK FOR DEBIAN REPOSITORY
# deb http://ftp.squeak.org/debian/ stable main
# deb-src http://ftp.squeak.org/debian/ stable main

## SCIM
# deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/

```

Or are the newest versions of python just not compatiable with the newest versions of python-dev??

---

