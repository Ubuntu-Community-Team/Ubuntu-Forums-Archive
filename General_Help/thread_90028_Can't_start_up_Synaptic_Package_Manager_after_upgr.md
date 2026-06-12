---
title: "Can't start up Synaptic Package Manager after upgrading"
date: 2005-11-14
forum: General Help
---

### Post by fei on 2005-11-14
After upgrading from Hoary to Breezy, I can't start up Synaptic Package Manager. I thought it's the source.list problem. So I just removed the file as empty and I still can't start up Synaptic. 

Can anyone help me with this??

---

### Post by Remmelas on 2005-11-14
if you start it from the terminal command line, does it give any helpful error output?

---

### Post by fei on 2005-11-14
started from command line, it says "Segmentation fault".

what should I do??

---

### Post by Remmelas on 2005-11-14
Hopefully someone can chime in who knows synaptic better than I do, but, to start, I'd do 
sudo apt-get install --reinstall synaptic
at the command line

---

### Post by fei on 2005-11-14
I rebooted the system. Now I can start synaptic and it asked for root password, and then died. After that, I tried to re-start up synaptic, it says Segmentation fault. Does it mean something wrong with source.list file or what???

---

### Post by Remmelas on 2005-11-14
out of curiosity, when you upgraded, did you apt-get dist-upgrade?  
bad sources.list files just get you lots of error message, not usually a segfault.

---

### Post by fei on 2005-11-14
I reinstalled synaptic. Stil won't work.

What should I do??

---

### Post by Remmelas on 2005-11-14
I'm unsure.  Again, hopefully someone who knows better can chime in, but synaptic segfaulting... not sure where to go from there.

---

### Post by fei on 2005-11-14
Another problem is I can't use "apt-get upgrade" neither.

I think I somehow broke package dependencies.

Here is my source.list file:
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```



Here is "apt-get upgrade output"
```

root@ubuntu:/home/fei # apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  totem
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


```

---

### Post by Remmelas on 2005-11-14
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list
```
and past in the following
```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

then do
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by fei on 2005-11-14
apt-get is working. but synaptic still not working.

What should I do??

---

### Post by DancingSun on 2005-11-24
I just upgraded to Breezy...and I have the exact same problem...reinstalling synaptic didn't help.

---

### Post by DancingSun on 2005-11-24
Ok, I found the culprit.

It appears that SCIM is conflicting with some of the gnome-based programs, after uninstalling SCIM, Synaptic and a couple other gnome programs will now run.

---

