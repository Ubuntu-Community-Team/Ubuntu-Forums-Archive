---
title: "Can't install package from apt"
date: 2008-08-16
forum: General Help
---

### Post by Nexusx6 on 2008-08-16
Hello,

A while back I had to install Virtualbox from the packages on the programs website because the ones that were in the repo's were not working on my system. Recently a dependency for virtualbox was released on the repo's, but because I didn't download VB via apt-get in the first place, I couldn't update this package from it (it kept giving me an error when I tried).

The other day I went ahead and used "Add/Remove Programs" to uninstall my copy of VB with the intent of doing a re-install through apt-get. Though I can't find any trace of VB now I still cannot install the packages from the repo's. This is the error I get
```
fox@aurora-project:~$ sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages

```

I really need to have VB so I can emulate Windows for a few key programs. I'd appreciate any help

---

### Post by Sycron on 2008-08-16
Please type the output of
> $ uname-r

---

### Post by jualin on 2008-08-16
Please post the output of your > cat /etc/apt/sources.list using the terminal

---

### Post by dje on 2008-08-16
try:
```
sudo apt-get install -f
```

dje

---

### Post by jualin on 2008-08-16
Or just download the precompiled Ubuntu package from the [Virtual Box]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") website. Good luck!

---

### Post by Nexusx6 on 2008-08-16
uname -r
```
fox@aurora-project:~$ uname -r
2.6.24-19-generic

```

```
fox@aurora-project:~$ **cat /etc/apt/sources.list**
## deb cdrom:[Kubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701.2)]/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hardy universe
deb-src http://archive.ubuntu.com/ubuntu hardy universe
deb http://archive.ubuntu.com/ubuntu hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu hardy-updates universe
deb http://archive.ubuntu.com/ubuntu hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu hardy-security universe

## Mediabuntu Sources
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free

## zman0900's PPA
deb http://ppa.launchpad.net/zman0900/ubuntu hardy main
deb-src http://ppa.launchpad.net/zman0900/ubuntu hardy main

```

```
fox@aurora-project:~$** sudo apt-get install -f**
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by dje on 2008-08-16
try:
```
sudo apt-get install virtualbox-ose-modules-2.6.24-20-generic
```
and then the command you used to try and install the first time

dje

---

### Post by Sycron on 2008-08-16
Since you have 2.6.24-19-generic i don't know why it says:
> Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed

:| really strange

try ```
apt-get install virtualbox-ose-modules-2.6.24-19-generic
``` and type the output.

---

### Post by Nexusx6 on 2008-08-16
>  	
Re: Can't install package from apt
Since you have 2.6.24-19-generic i don't know why it says:
Quote:
Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
really strange

try
Code:

apt-get install virtualbox-ose-modules-2.6.24-19-generic

and type the output. 

Whoa, that is really strange! I didn't catch that at all, good eyes lol. I went ahead and specified that I wanted the *-19-generic modules and they installed fine. Then I ran the rest of the of the packages through apt-get
```
sudo apt-get install virtualbox-ose virtualbox-ose-source
```
And now those too have installed fine. I need to logout so that I am part of the right group to run VB... but I think every is installed fine :D

---

### Post by Nexusx6 on 2008-08-16
Yay! It works! God I love these forums :D Thanks for the help everyone

---

### Post by Sycron on 2008-08-16
If your problem is solved you may go to thread tools and mark your thread as solved.

---

